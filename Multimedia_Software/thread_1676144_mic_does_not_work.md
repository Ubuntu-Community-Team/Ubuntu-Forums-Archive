---
title: "mic does not work"
date: 2011-01-26
forum: Multimedia Software
---

### Post by badnaam on 2011-01-26
My microphone does not work across applications (google voice, sound recorder etc).

Here is my ubuntu version


2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

Alsa version

Advanced Linux Sound Architecture Driver Version 1.0.23.

I have tried all sorts of things including reinstalling alsa driver and utilities, insuring the input mic is not mute, adjusting the left/right channels etc.

What else can I do?

Thanks!

---

### Post by gordintoronto on 2011-01-26
Did you run alsamixer to jack up the mic levels?

---

### Post by badnaam on 2011-01-27
Yes I did, no luck there

---

### Post by lidex on 2011-01-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

