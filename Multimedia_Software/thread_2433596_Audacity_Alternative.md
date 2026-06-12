---
title: "Audacity Alternative?"
date: 2019-12-21
forum: Multimedia Software
---

### Post by lwalper on 2019-12-21
I've been using Audacity in Win10 for some time now and it works great. I keep trying to develop a love for Ubuntu, but am having trouble gaining an appreciation for its power and Windows liberty. In my quest for freedom from Windows I've again installed 18.04 and am having trouble running Audacity. I've installed FFMPEG and am still unable to open a mp3 file. Where's Lame? Is it no longer available for Ubuntu? Is there an alternative to Audacity? I installed Ardour, but it won't read the mp3 file either.

Help!

---

### Post by CatKiller on 2019-12-21
You don't need an alternative to Audacity if that's what you're used to using. For Audacity to be able to open mp3 files you need an mp3 audio codec, which isn't able to be freely distributed with Ubuntu because of patent issues primarily in the US. You can install the **ubuntu-restricted-extras** package to gain that functionality, or the **libavcodec-extra** package directly if you're only interested in the codecs rather than fonts and whatnot.

---

### Post by lwalper on 2019-12-21
And where are these codecs to be found? I've checked the Ubuntu software tab and checked the "Help" button - no help there?

---

### Post by CatKiller on 2019-12-21
```
sudo apt install ubuntu-restricted-extras
```

---

### Post by lwalper on 2019-12-21
OK. So I found the Synaptic installer gadget and found the codecs there. Thanks!

---

### Post by lwalper on 2019-12-21
So, installed the codecs and extras (and FFMPEG) and still get the dreaded "did not recognize the type of the file" warning. Hmmm?? What's up with that?

---

### Post by Dennis N on 2019-12-21
The mp3 patent expired in 2017. 
According to Audacity Manual:

> The audio formats importable by Audacity with the File > Import > Audio... command, as shipped are:
For uncompressed audio: most WAV and AIFF files including all PCM variants can be imported into Audacity
Compressed audio: Ogg Vorbis, FLAC, MP2 and MP3 can be imported into Audacity. 
I don't have ffmpeg or lame installed, and I have no problem importing and playing an mp3 file using Audacity without them. (You wouldn't need lame to play a file, since lame is an encoder for mp3). Does your file not load or not play or both? Does a visible sound plot load into the editing window?

If you just want a good player, use Audacious. It has many codecs built in.

---

### Post by lwalper on 2019-12-22
The file plays OK - in Totem I suppose. Audacity will not import the mp3 file. It won't import wav files either. I get the same warning telling me maybe I should try installing FFmpeg (which I've already done. Just tried reinstalling Audacity - no joy - installs OK, but same problem. I was reading on another thread that Audacity doesn't play well together with 18.04. Maybe that's it?? So, is there another audio editor that works?

---

### Post by CatKiller on 2019-12-22
> **lwalper said:**
> I was reading on another thread that Audacity doesn't play well together with 18.04. 

I just installed it on my 18.04 machine to check and mp3 import works perfectly straight away.

If you've installed Audacity as a snap it might not be able to read from wherever you've got your mp3s.

---

### Post by lwalper on 2019-12-22
OK, that fixed it. I'm working on a dual boot machine and was reading from the Windows partition. Moved the file from there to the Ubuntu partition and it works fine.

---

