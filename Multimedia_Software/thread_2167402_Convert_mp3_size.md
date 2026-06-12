---
title: "Convert mp3 size?"
date: 2013-08-13
forum: Multimedia Software
---

### Post by borgward on 2013-08-13
How, or can I convert mp3 file to smaller size?

---

### Post by GwL3eNC on 2013-08-13
A lower bitrage should result in a smaller file with lower quality. You can use lame for this purpose.

---

### Post by slickymaster on 2013-08-13
You can use [lame]("http://lame.sourceforge.net/"). You give it an mp3 file, specify a new (lower) bitrate and an output file and you get a new, smaller mp3.
```
lame --mp3input -b 80 input.mp3 output.mp3
```
But be advised, shrinking the mp3 will reduce it’s sound quality.

---

### Post by varunendra on 2013-08-13
If you are going to play the file on computer only, it is better to convert it to AAC. It gives the same quality at a bitrate of 64 kbps that mp3 gives at 128 kbps, which means the same quality in half the size.

However, conversion from one lossy format to another is always going to lose some quality.

You can install "nautilus-script-audio-convert" script from the repository to easily convert files from one format to another. "Soundkonverter" seems to be an even better (GUI) application for the same job, but I don't know whether it supports AAC or not.

***EDIT :** Just tried "soundkonverter" myself. It is really nice and gives granular level control over the conversion under "Detailed" tab of its GUI.*

---

