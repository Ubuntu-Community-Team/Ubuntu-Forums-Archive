---
title: "Need Help With Sound/Headphones!!!"
date: 2010-10-28
forum: Multimedia Software
---

### Post by wipeoutking on 2010-10-28
Hey. I am having this problem with 10.04 LTS Ubuntu. When i have my headphones plugged in and i adjust the volume on the computer the sound of the music flows threw the headphones AND the speakers on the computer. It is soooo annoying and i don't know how to fix it. :( Could you please help me!?
Thank you!

---

### Post by keibee on 2010-10-28
Have a look at this: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/637040]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/637040")

I solved exactly the same problem with this.  It can take a while to find out which option works. On my Acer Aspire One 521 it turned out to be the "thinkpad" option.

Keibee

---

### Post by lidex on 2010-10-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by mcoleman44 on 2010-10-28
if that doesnt work there is a really quick but temporary fix. Go to sound options and change the output to just the headphones. But you would have to change this every time you plugged or unplugged your headphones

---

