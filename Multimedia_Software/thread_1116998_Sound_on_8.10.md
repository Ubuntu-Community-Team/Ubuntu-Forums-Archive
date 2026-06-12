---
title: "Sound on 8.10"
date: 2009-04-05
forum: Multimedia Software
---

### Post by FwinTlin on 2009-04-05
It's about a week now that I've installed ubuntu 8.10. After installing all updates, the sound became very silent (volume is at max but I hardly can hear anything). I've been searching the forums for solutions but none of them worked. Any ideas? Thanks in advance.

---

### Post by null.byte on 2009-04-05
Go to the Volume Control, and check if PCM and/or Front are at maximum value:

[http://img134.imageshack.us/img134/2024/screenshotvolumecontrol.png](http://img134.imageshack.us/img134/2024/screenshotvolumecontrol.png)

---

### Post by FwinTlin on 2009-04-05
Yes, both at maximum.

---

### Post by null.byte on 2009-04-05
System > Preferences > Sound

Set everything to ALSA.

---

### Post by FwinTlin on 2009-04-05
Changes nothing.

---

### Post by null.byte on 2009-04-05
sudo apt-get install alsamixergui
alsamixergui

---

Try raising Masters from there.

---

### Post by FwinTlin on 2009-04-05
At maximum already.

---

### Post by corpsehacker on 2009-04-05
Did the updates include any drivers for a sound card? I had an incedent once where the auto update downloaded and installed a non-linux driver for my graphics card. As a result I had no video and had to format my harddrive and reinstall Linux. It was a huge pain. Best of luck to you.

---

### Post by null.byte on 2009-04-05
Did you try this? [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Try Part C.[SIZE=4][/SIZE]

---

### Post by FwinTlin on 2009-04-05
Nothing.

---

### Post by null.byte on 2009-04-05
Bump... can someone please take this issue on? It goes beyond my knowledge.

---

### Post by markbuntu on 2009-04-05
Troubleshooting is here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by FwinTlin on 2009-04-06
Sigh.. Still can't get it working.. The longer I try, the more I start to believe I'm missing something very obvious... Any more ideas?

---

### Post by FwinTlin on 2009-04-06
Bump...

Well I don't know if this is important but if I set my speakers volume to max there's a weird noise (like it was vibrating from too much power) and when ubuntu loading bar is at ~30% that sound goes away.. So... Yeah.. Any help is still welcome..

---

### Post by FwinTlin on 2009-04-07
Another bump..

---

