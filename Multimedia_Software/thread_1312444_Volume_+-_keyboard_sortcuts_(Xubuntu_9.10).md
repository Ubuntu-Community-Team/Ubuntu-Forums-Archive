---
title: "Volume +/- keyboard sortcuts (Xubuntu 9.10)"
date: 2009-11-03
forum: Multimedia Software
---

### Post by sitruuna on 2009-11-03
I just did a clean install of Xubuntu 9.10

I have an USB headset connected to my PC. I got sound working but now when I try to control volume with +/- multimedia keys, it doesn't change my Speaker volume. It changes my Mic volume.

How I can set it to change my speaker volume.

And another problem: when I try to run alsamixer in terminal I get:

alsamixer: function snd_ctl_open failed for default: No such file or directory

---

### Post by Anonymousable on 2009-11-03
System>Preferences>Keyboard shortcuts

Should be there (if the multimedia keys are processed as part of the keyboard)

---

### Post by sitruuna on 2009-11-03
> **Anonymousable said:**
> System>Preferences>Keyboard shortcuts

Should be there (if the multimedia keys are processed as part of the keyboard)

I have **Xubuntu** (xfce) not Ubuntu (gnome)

The problem is that xfce4-volumed controls my mic volume instead of speakers volume

---

### Post by sisco311 on 2009-11-03
Right click on the panel's Mixer applet -> Properties -> Mixer track -> Master (or PCM)

---

### Post by sitruuna on 2009-11-03
> **sisco311 said:**
> Right click on the panel's Mixer applet -> Properties -> Mixer track -> Master (or PCM)
The mixer applet is working and controlling my Speaker volume, but xfce4-volumed (multimedia keys) still control my Mic volume. :S

---

