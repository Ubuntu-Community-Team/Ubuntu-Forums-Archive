---
title: "convert ape file to wav using avconv"
date: 2014-07-17
forum: Multimedia Software
---

### Post by humanracer on 2014-07-17
Hi I am using avconv as ffmpeg isn't available in Ubuntu 14.

I tried avconv -i input.ape output.wav but I got the error "unable to find a suitable output format"

Any ideas?

---

### Post by FakeOutdoorsman on 2014-07-22
avconv is buggy. Try [downloading ffmpeg](http://ffmpeg.org/download.html) (get a static build). Does it also give you the same issue? If yes, then please show your command and complete console output.

---

### Post by palmgrower on 2014-09-15
Open abc.ape in audacity. Export to flac/wav/mp3 or whatever.

---

### Post by shantiq on 2014-09-17
if all you wish for here is to decompress/return to wav  your ape files   use

```
sudo apt-get install mac
``` to install ape on your system mac means MonkeyAudioCodec

Or install through a [deb]("http://ubuntuforums.org/attachment.php?attachmentid=192966&d=1306154095")


 cd    to your folder of ape files then  then run:


```
for f in *.ape; do mac "$f" "${f%.*.ape}.wav" -d  ; done

```

and you will obtain


```
--- Monkey's Audio Console Front End (v 3.99) (c) Matthew T. Ashland ---
Decompressing...
Progress: 100.0% (0.0 seconds remaining, 11.5 seconds total)          
Success...
--- Monkey's Audio Console Front End (v 3.99) (c) Matthew T. Ashland ---
Decompressing...
Progress: 100.0% (0.0 seconds remaining, 13.0 seconds total)          
Success...

```

---

### Post by palmgrower on 2015-01-29
[code]for f in *.ape; do mac "$f" "${f%.*.ape}.wav" -d  ; done[end code]

This command did the conversion, but the long file name is gone. For instance, "12. Tchaikovsky Nutcracker Suite.....,ape" is converted to "12.wav"

EDIT: I got it right. [code]for f in *.ape; do mac "$f" "${f%.ape}.wav" -d  ; done[end code]

Also, if the music in external hard disk, cd /media/[tab key] and continue to add first few letters. For example, cd /media/[tab key] > john > cd /media/john/[tab] > Music 1 Photo 2 Video 1 Video 2.... > cd /media/john/Mu/[tab] >cd /media/john/Music\1/.....

---

