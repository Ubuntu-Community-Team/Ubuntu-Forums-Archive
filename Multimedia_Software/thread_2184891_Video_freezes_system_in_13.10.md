---
title: "Video freezes system in 13.10"
date: 2013-10-31
forum: Multimedia Software
---

### Post by marinecomm on 2013-10-31
No matter what format or what video player I use, every time I try to play a video off my computer while running 13.10 causes the whole system to freeze up. No mouse movement or anything. I can't even Ctrl + Alt + Delete out. I made sure I had:

1. all the necessary codecs
2. that I had xubuntu-restricted-extras installed
3. I went to Software & Updates and made sure that 'Software restricted by copyright' and 'Proprietary drivers' were both checked
4. I switched video drivers from the proprietary AMD driver to the X.org x server video driver

Nothing has helped so far. I have tried several videos of different formats and tried several players. I was running 12.04 and everything worked fine. I never had any video issues at all. Any thoughts or suggestions? Again, I'm running Xubuntu 13.10 64-bit.

---

### Post by shantiq on 2013-11-01
run ```
metacity --replace
```    to check if it works when on Gnome

then later   to return to unity run  ```
unity --replace &
```


i had similar problems and then changed [Desktop Environment]("http://ubuntuforums.org/showthread.php?t=2181390&p=12835406#post12835406") to cure that

---

### Post by marinecomm on 2013-12-04
I fail to see what GNOME and Unity have to do with Xubuntu. I'm not using either of those.

---

### Post by deadflowr on 2013-12-04
Yeah, gnome and unity and xubuntu are like water oil and vinegar.

Maybe this can help you diagnose the problems
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by marinecomm on 2013-12-04
None of those seem to be what I am experiencing. If it were a GPU issue then wouldn't I have come across it in 12.04? I had no issues playing videos in 12.04. I have even used Lubuntu 13.10 and it plays videos without freezing so it has to do with Xubuntu 13.10 itself.

---

### Post by bookrt on 2014-03-02
I am experiencing the same issue after upgrade to XUbuntu 13.10. I had experienced similar issues using Linux Mint 16 but switching to XUbuntu 12.04 LTS seemed to have solved the problem. Directly after upgrade I have started getting graphics freezes in Google Chrome and while playing Minecraft. In Minecraft it is every 5-10 minutes. My system is Celeron G540 and Biostar H77MU3. I have tried upgrading graphics drivers using the Intel installer and the freezes are still happening.

---

