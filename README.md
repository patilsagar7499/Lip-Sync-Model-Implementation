# Lip-Sync-Model-Implementation

This repository contains a **Google Colab Notebook** to implement **Wav2Lip** for lip-syncing an image with an audio file. It also includes steps for converting text to speech using Python.

## 🚀 **Colab Preliminaries**

Before starting, make sure you have access to **Google Colab** and **Google Drive** to store necessary files.

1. Open Google Colab.
2. Mount Google Drive:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

---

## 📥 **Get the Code and Models**

1. Clone the Wav2Lip repository:
   ```bash
   !git clone https://github.com/Rudrabha/Wav2Lip.git
   ```

2. Navigate to the Wav2Lip folder:
   ```bash
   %cd Wav2Lip
   ```

3. Download the pre-trained model (`wav2lip.pth`) and place it inside `Wav2Lip/checkpoints/`:
   ```bash
   !wget "https://storage.googleapis.com/wav2lip/models/wav2lip.pth" -O checkpoints/wav2lip.pth
   ```
   Or manually upload the model to Google Drive and copy it:
   ```bash
   !cp "/content/drive/My Drive/wav2lip.pth" "checkpoints/wav2lip.pth"
   ```

---

## 📦 **Get the Pre-requisites**

1. Install required dependencies:
   ```bash
   !pip install -r requirements.txt
   ```

2. Ensure the correct **Python version**:
   ```bash
   !python --version  # Should be Python 3.7 or 3.8
   ```

3. Install compatible **OpenCV versions**:
   ```bash
   !pip install opencv-python==4.5.5.64 opencv-contrib-python==4.5.5.64
   ```

---

## 🎙 **Converting Text to Audio**

Before running Wav2Lip, generate an **audio file** from text using **gTTS (Google Text-to-Speech)**:

```python
from gtts import gTTS
text = "Hello! This is a test audio for lip-syncing."
tts = gTTS(text, lang='en')
tts.save("input_audio.wav")
```

This will generate an `input_audio.wav` file.

---

## 🛠 **Implementation!**

Run Wav2Lip to generate a lip-synced video:
```bash
!cd Wav2Lip && python inference.py \
    --checkpoint_path checkpoints/wav2lip.pth \
    --face "../sample_data/input_photo.png" \
    --audio "../sample_data/input_audio.wav"
```

---

## 🎯 **Expected Output**

If everything is set up correctly, the final lip-synced video will be generated in the `results/` directory.

**Example Output:**
```
Using CPU for inference.
Reading video frames...
Number of frames available for inference: 1
Generating lip-sync video...
Saved output video to results/final_output.mp4
```

---

## ✅ **Notes**

- If you face issues like **module not found**, try reinstalling dependencies with:
  ```bash
  !pip install -r requirements.txt --upgrade
  ```
- Ensure `wav2lip.pth` is not corrupted by checking its file size (~346MB).

📌 **Now you're ready to use Wav2Lip for lip-syncing any image with audio! 🎬🎙**

