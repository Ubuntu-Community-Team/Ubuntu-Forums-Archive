---
title: "lame command"
date: 2008-09-19
forum: Multimedia Software
---

### Post by dolecek1 on 2008-09-19
hello I'm new to linux....I'm trying to convert a 320k mp3 to a 128k mp3 using lame but i cant figure out the exact command....could someone please tell me the exact command for this?

---

### Post by mc4man on 2008-09-20
Putting aside the advisability of lossy to lossy conversions, there are many ways to tweak parameters and just as many opinions. Ultimately it's what suits you. I would say try the easiest method first and take it from there.
One of the easiest would be to install Sound converter  ```
sudo apt-get install soundconverter
``` or look in synaptic.

open it from applications menu -> sound&video. It's pretty self explanitory, either add single tracks or a folder of tracks. Just don't save in same folder. A decent setup is in screen, access settings from edit -> preferences. It will keep all the tags, track names ect.

If the result is good for you** great, otherwise look in ```
lame --longhelp
``` and or post your parameters

---

### Post by dolecek1 on 2008-09-20
i tried soundcoverter and i converted the files and even tho i specified 128k it took it clear down to 120k instead of 128k,  i did get lame to work tho,found out lame is very stable while soundconverter is not

---

