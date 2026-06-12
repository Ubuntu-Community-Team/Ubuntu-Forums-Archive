---
title: "Problems with sound in Flash / Youtube videos"
date: 2008-09-03
forum: Multimedia Software
---

### Post by Blinky981 on 2008-09-03
For some reason, I can't get any sound in youtube videos, or any other flash for that matter... I have the Adobe Flash plugin installed for Firefox, so I can actually "play" the video... Just no sound.

I can get sound in any other application, and after following part of the comprehensive tutorial sticky, multiple applications at a time (e.g. Pidgin notifications and Rythmbox)

I tried "aoss firefox" after installing the alsa-oss package, but that hasn't made any difference whatsoever. The problem can't be Firefox itself, because the fire.fm plugin is working fine (and I've got a funny feeling that is flash-based too, because it won't work without the flash plugin installed)

So yeah, I'm confused... any ideas?

---

### Post by loconet on 2008-09-05
I had this problem a few minutes ago, fixed it by installing libflashsupport:


```
sudo apt-get install libflashsupport
```

---

### Post by xpd259 on 2008-09-06
worked for me .. thanks  :0D

---

### Post by dnpate on 2009-03-10
Does not work for me.
Any other ideas?
David

---

### Post by Prixos on 2009-03-11
> **loconet said:**
> I had this problem a few minutes ago, fixed it by installing libflashsupport:


```
sudo apt-get install libflashsupport
```

Wow, after all those trail-and-errors this one worked instantly! Thank you very much.

---

### Post by Shii on 2009-03-17
> **loconet said:**
> I had this problem a few minutes ago, fixed it by installing libflashsupport:


```
sudo apt-get install libflashsupport
```
I have no idea why installing a library should change anything, but this worked like magic! Thanks!

---

### Post by gandaran on 2009-03-17
> **Shii said:**
> I have no idea why installing a library should change anything, but this worked like magic! Thanks!
all of you must be using adobe flash 9, libflashsupport is just to fix the sound issue with flash 9 but there is another way upgrade to flash 10 and you wont need libflashsupport installed.

---

### Post by sjvega on 2009-03-19
Hi, I'm having the same problem and i tried to remove the flash package an reinstallit, or install th one on the adobe page, and of course install the libflashsupport, but still no sound, any ideas?
Thanks

---

### Post by gandaran on 2009-03-19
> **sjvega said:**
> Hi, I'm having the same problem and i tried to remove the flash package an reinstallit, or install th one on the adobe page, and of course install the libflashsupport, but still no sound, any ideas?
Thanks
fix pluseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by sjvega on 2009-03-19
Thanks, it worked, but i can't seem to save the configuration i did, so i was wondering if there was a way to do it, I don't want to configure everything each time I boot.

---

