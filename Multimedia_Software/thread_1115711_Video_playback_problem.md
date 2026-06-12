---
title: "Video playback problem"
date: 2009-04-04
forum: Multimedia Software
---

### Post by Janjiss on 2009-04-04
Hello! 

I ran in one issue. When i playback video in full screen it is getting laggy. It must not be related to video drivers, becuse i tried to pal video with enabled drivers and disabled. It must not be an special effects issue to. Tried to install 8.10 and 8.04 Both Kubuntu and Ubuntu. It isn ot only flash problem, it is avi, divix file problem 2...


Thnx

---

### Post by xc3RnbFO8P on 2009-04-04
What is your computer spec.?
In Terminal (show the output):
> lspci | grep VGA

---

### Post by deboare on 2009-04-04
> **Ringi said:**
> What is your computer spec.?
In Terminal (show the output):

I have a similar problem, with any media player and the output of that is:
02:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro]

---

### Post by xc3RnbFO8P on 2009-04-04
Can you post your xorg.conf:
> gedit /etc/X11/xorg.conf

---

### Post by deboare on 2009-04-04
> **Ringi said:**
> Can you post your xorg.conf:
I think by executing that command I created the file, because it is empty and when I exit the editor it asks me to save.
I should also mention that I switched my video output (gstreamer-properties) to X Window System (No Xv).

Thanks :)

---

