---
title: "Soundconverter command line: setting bitrate"
date: 2011-08-29
forum: Multimedia Software
---

### Post by CommuSoft on 2011-08-29
Hi,

I want to convert a lot of .wav files to .mp3. Because the quality doesn't matter and the sound files are relativly long, I would like to convert it to "very low" quality with variable bitrate (VBR). The options are available in Soundconverter. Are there any options to do this by the command line.

Currently I have the following bash command:

```
soundconverter -b -m audio/mpeg -q -s .mp3 "$f.wav"
```

I was wondering if there are other options available to edit the bitrate (Haven't found any in the man page). The program doesn't have to be Soundconverter. If there is a better program with bash commands.

Thanks in advance.

---

### Post by ron999 on 2011-08-29
> **CommuSoft said:**
>  The program doesn't have to be Soundconverter. If there is a better program with bash commands.

Hi
If you only want to convert wav files to mp3 you might as well use **LAME**.
```
sudo apt-get install lame
```

Then use [FONT="Courier New"]**lame --longhelp**[/FONT] to see the options.

---

### Post by CommuSoft on 2011-08-30
Many thanks! That program did the job :D

---

