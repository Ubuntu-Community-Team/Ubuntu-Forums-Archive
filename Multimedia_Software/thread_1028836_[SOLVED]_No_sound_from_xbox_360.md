---
title: "[SOLVED] No sound from xbox 360"
date: 2009-01-02
forum: Multimedia Software
---

### Post by celtic426 on 2009-01-02
Hey guys,

I'm having this problem with connecting my xbox 360 to my monitor (don't worry, this relates to ubuntu).  I have my xbox going to my monitor with a vga cord and then the sound going into my computer from my xbox thru a quarter inch cable plugged in to line in port on my motherboard's integrated sound card (realtek alc850).  When I run Windows on my computer, sound works.  When I run ubuntu, sound doesn't.  So I'm wondering what I can do to fix this.  

I don't have really any experience with troubleshooting sound in linux so I don't really know where to begin.  If someone could help me with this, that would be great.  

I'm not running striaght ubuntu, it's actually crunchbang linux, which is basically built off ubuntu but uses openbox as a display manager.  So I do not have all the default packages that come with ubuntu, some of which possibly could make the sound work?  I do not know.  And yes sound in general works on my ubuntu OS, like if I want to play music and stuff, it's just the xbox 360 sound that doesn't come thru.

Please someone help, and if you need more info, just ask.  Thanks.

---

### Post by celtic426 on 2009-01-04
I fixed it.  I just had to run "xfce4-mixer" and then unmute the line in switch.

---

