---
title: "Devices are switching places in /dev/"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by dZag on 2006-12-31
Hello
First i like to sorry for my English.... 
I have problems with multimedia devices. In my computer there are installed SB Live, Aver TV card and Labtec Webcam. Basicly these devices are switching places in /dev. For example:
AverTv is /dev/video0
Labtec Cam is /dev/video1, 
after rebooting these two devices are switched:
AverTv is /dev/video1
Labtec Cam is /dev/video0
In various programs i have to change settings of video devices becouse they show wrong output after reboot.
I have similar problem with sound card (switching between SB LIVE, AverTV) and remote control(switching with mice or keyboard). Is there any way to permanently assign device to specified file in /dev.
Thanks...

---

### Post by damvcoool on 2007-01-14
I've been having exactly the same problem since i move to edgy.

can anyone help!!!

---

### Post by dleroy on 2007-11-07
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif) [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif) I am also having this problem my /dev/video0 and video1 keep switching in boot. I seen a fix for this some place while working on a different problem, but don't seem to remember where it was. somthing to do with module.conf I think.

---

