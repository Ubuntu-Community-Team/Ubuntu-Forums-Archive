---
title: "How to fix/repair WAV under ubuntu ?"
date: 2015-10-26
forum: Multimedia Software
---

### Post by alain.roger on 2015-10-26
Hi,

i have several wav files with several hundreds of MB.
when i open them in audacity it seems they are empty while i can play them on my Samsung S5 neo.
Please how can i fix/repair them under ubuntu ? Is there any application or command line to do it ?

thx

---

### Post by slickymaster on 2015-10-26
Moved to the **Multimedia Software** sub-forum, which is the the place for your multimedia software questions: everything about using software for audio, video and image editing, display, or viewing and listening.

---

### Post by Yellow Pasque on 2015-10-26
Can you run mediainfo on one of the wav files?
```
sudo apt-get install mediainfo
mediainfo example.wav
```

Does audacity produce any error messages when you start it in the terminal and load a wav?

---

### Post by masdeal on 2015-10-26
Here, try this:
hxxp://manpages.ubuntu.com/manpages/hardy/man1/qwavheaderdump.1.html

---

### Post by kryten35 on 2015-10-27
VLC media player can output wav.Try running one of your files through it to see if it fixes the problem that audacity has with them.

Media>Convert/Save>Add     For profile  select  Audio-cd  which is wav.

Also  Tools>codec information  will give you details about the audio.

---

### Post by alain.roger on 2015-10-27
> **Temüjin said:**
> Can you run mediainfo on one of the wav files?
```
sudo apt-get install mediainfo
mediainfo example.wav
```

Does audacity produce any error messages when you start it in the terminal and load a wav?

mediainfo returns only filename and filesize... nothing more about file

---

### Post by alain.roger on 2015-10-27
After doing several tries, i finally was able to import as RAW data the wav in Audacity as Signed 16 PCM, mono channel and with 16000Hz. Now data is ok and i can listen to first damaged audio without any issue.

---

