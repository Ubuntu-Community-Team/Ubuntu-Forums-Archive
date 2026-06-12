---
title: "Creative Labs sound Card Compatibility?"
date: 2006-05-09
forum: Multimedia &amp; Video
---

### Post by shurguywutt on 2006-05-09
I am pretty new to Ubuntu, and everything seems to be working pretty well except I cannot get any sound from my Creative sound card (Creative Sound Blaster Live! 24-bit (SB0410) Internal PCI - VAR).  I am running both Ubuntu and XP professional, sound works fine on Xp Pro, but I dont get anything when I switch to Ubuntu.  Can anybody help me out?  Thanks.[EMAIL="bcm663@aol.com"]bcm663@aol.com[/EMAIL]

---

### Post by glotz on 2006-05-09
Here's something but it's greek to me [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)

---

### Post by shurguywutt on 2006-05-10
It says that my soundcard is compatible, but obviously not because its not working.  Do you think I should try and install the drivers?

---

### Post by glotz on 2006-05-10
I guess it couldn't hurt you. Might be wrong. Just a newbie myself.

---

### Post by Sutekh on 2006-05-10
According to the [ur=http://www.alsa-project.org/alsa-doc/]ALSA Soundcard Matrix[/url], your soundcard is supported (I have one too).

 - Start by checking that you have the sound modules loaded
```
lsmod | grep snd
```Hopefully there will be some modules such as **snd-ca0106**

 - If they are not present you should follow the guide to installing them

[ALSA - SB Live 7.1 (SB0410) Driver Instructions](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106)


 - Also check that all your channels are unmuted with the ALSA mixer
```
alsamixer
```

---

