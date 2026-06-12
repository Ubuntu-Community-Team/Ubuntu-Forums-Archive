---
title: "No sound with HDA-Intel (High defination audio) - ALC861"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by Jimmyqwy on 2006-10-25
I tried several different kernels and different ALSA versions, namely 1.0.12 and 1.0.13. But with all of them, the speakers stay silent.
My sound card is HDA-Intel (High defination audio) - ALC861
Does anyone have any suggestion?
Reply With Quote

---

### Post by ReaderRat on 2006-11-09
> **Jimmyqwy said:**
> I tried several different kernels and different ALSA versions, namely 1.0.12 and 1.0.13. But with all of them, the speakers stay silent.
My sound card is HDA-Intel (High defination audio) - ALC861
Does anyone have any suggestion?
Reply With Quote

I have a Toshiba Satellite laptop with ICH7 Intel HDA (High Definition Audio).
I now have sound after 3 weeks. I got it by using [**[color=RED]This Comprehensive Guide[/color]**](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

The driver was hda-intel .

---

### Post by mstrat on 2006-11-09
I had this same problem with a Toshiba laptop, when I upgraded to Edgy, problem was solved...

---

### Post by starorbs on 2006-11-10
I have no idea what's causing your specific problem, but give this a try.
Add this line to /etc/modprobe.d/alsa-base:
options snd-hda-intel position_fix=1 model=laptop-eap

When I added this and then restarted I had sound on my Asus W3J laptop. I still wouldn't have sound today if I didn't find some random archived thread on some forum.

Also if that didn't work type "alsamixer" in the terminal and make sure Master,PCM, and external are NOT muted. That's what's giving me sound.

Good Luck.

---

