---
title: "Jaunty 9.04 Web Video"
date: 2009-06-04
forum: Multimedia Software
---

### Post by burpootus on 2009-06-04
I currently have adobe-flashplugin and flashplugin-nonfree installed, no SWF or Gnash. I also have the ubuntu-restricted-extras installed. I have tried several different combinations of plugins and I am unable to watch videos on CNN.com or Nascar.com. Youtube videos work. Not being able to watch internet videos at will is becoming a real drag, and to make it worse, on some of them you can watch the commercial and then not the video itself. Can anyone help me with this problem?

---

### Post by pawnrocket on 2009-06-04
Try 

```
sudo apt-get remove flashplugin-nonfree && apt-get install flashplugin-nonfree
```

Log out and back in

Also what model of graphics card? Intergrated or not?

---

### Post by burpootus on 2009-06-04
> **pawnrocket said:**
> Try 

```
sudo apt-get remove flashplugin-nonfree && apt-get install flashplugin-nonfree
```

Log out and back in

Also what model of graphics card? Intergrated or not?


Tried that, no luck. Running Nvidia card, top of the line from January 2006 (I forget the model number). I downgraded from 180 driver to 173, same result with videos.

---

### Post by pawnrocket on 2009-06-04
Did you log out and in?

Do you have any add-ons in firefox?

---

### Post by burpootus on 2009-06-05
> **pawnrocket said:**
> Did you log out and in?

Do you have any add-ons in firefox?


Yes, I even restarted. I have Windows Media Player plugin 10, VLC Multimedia plugin, Shockwave Flash 10.0 r22, Quicktime plugin 7.2.0, Java 1.6.0_b03, and DIVX Web Player plugin. I tried turning these off (except for flash) and still the same result.

---

### Post by lapichiflati on 2009-06-05
I was experiencing similar playback issues with flash on some sites but not others, or even selected bits of flash on a site but not all of it.    Experiment with disabling add-ons if you have any enabled.  This was the solution for me.

---

### Post by burpootus on 2009-06-06
> **lapichiflati said:**
> I was experiencing similar playback issues with flash on some sites but not others, or even selected bits of flash on a site but not all of it.    Experiment with disabling add-ons if you have any enabled.  This was the solution for me.


I've tried to troubleshoot this in a step by step manner. I again disabled add ons and found that nascar.com videos would play, cnn.com will not. A step in the right direction. I re-enabled each add on and I can still play nascar.com and not cnn.com videos, so much for step by step troubleshooting, it must've been something else I changed that gave me nascar.com videos. I still can't view cnn videos, what's the trick to them?

---

