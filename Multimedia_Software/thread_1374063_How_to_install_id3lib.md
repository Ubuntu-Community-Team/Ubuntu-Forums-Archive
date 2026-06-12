---
title: "How to install id3lib"
date: 2010-01-06
forum: Multimedia Software
---

### Post by connel on 2010-01-06
My PS3 for some reason does not play some of my mp3s so I wanted to encode them to normal mp3s using Kubuntu.

I have installed a program called audiokonverter (available from [http://www.kde-apps.org/content/show.php?content=12608]("http://www.kde-apps.org/content/show.php?content=12608")) that I have used to successfully encode my old mp3s to new mp3s that do play on my ps3. However none of the mp3 tags are being copied to the new files. So I noticed a requirement of  audiokonverter was id3lib. I couldn't find a package called id3lib in Synaptic but I did install a program called libid3-3.8.3-dev. audiokonverter displays the following in a terminal when running:

> **ID3v2 found. Be aware that the ID3 tag is currently lost when transcoding.**
LAME 3.98.2 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
CPU features: MMX (ASM used), SSE (ASM used), SSE2
Using polyphase lowpass filter, transition band: 19383 Hz - 19916 Hz
Encoding /home/me1/file.mp3
      to /tmp/audiokonv27390.wav
Encoding as 44.1 kHz j-stereo MPEG-1 Layer III (5.5x) 256 kbps qval=2
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA
  6435/6435  (100%)|    0:21/    0:21|    0:21/    0:21|   7.8331x|    0:00
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   kbps        LR    MS  %     long switch short %
  256.0       44.7  55.3        89.8   5.4   4.8
Writing LAME Tag...done
ReplayGain: -9.7dB
Parsing /home/me1/me2/file.mp3: done.  Copying to /tmp/audiokonv27390.wav: done
**Copied ID3 tag.**

The resulting mp3 file still has its album art, year, track number, album artist and Composer tags  but the song title, artisit, album and genre are filled with weird symbols (strangely if I copy these strange symbols from (for example) the artist field from a wine program called mp3tag and paste them into open office writer the correct artist is pasted :s. Yet if I add the file to my JuK library the song title and artist etc are all weird Chinese style symbols. I have tried installing id3lib from source but get the following error when I type sh ./configure

> configure: error: Missing a vital header file for id3lib

Someone please help me!!!! lol

---

### Post by connel on 2010-01-09
Bump!!

---

### Post by TenTin on 2010-06-18
BUMP! I have this problem too, and this is driving me nuts!
It show okay on gedit and the explorer, but show squares with numbers in them when I play them on music players like banshee and rhythm box. Both chinese and Japanese songs, any help would be appreciated!

---

