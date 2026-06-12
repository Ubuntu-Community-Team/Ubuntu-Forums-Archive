---
title: "Sound Driver for 5.1 channel"
date: 2009-06-13
forum: Multimedia Software
---

### Post by supravat on 2009-06-13
Hi, I have installed Ubuntu 9.04 in my computer. I have a motherboard of intel Gigabyte-s series. I have a sound system that have 5.1 channels. But when I am playing any audio/video file using totem movie player it only gives me sound output of 2.1 channel, other speakers gives no output. I have also configured the following option totem movieplayer > edit > plugins > audio > 5.1 channels. but this is not working.

Please help me...

---

### Post by expelledboy on 2009-06-14
-right click the volume-adjuster applet
-select **Open Volume Control**
-press the **Preferences** button
-make sure all the right channel are checked (Front, Side, Center.. etc)
-if they are muted unmute them :)

---

### Post by fooman on 2009-06-14
have a look at this guide:

[http://ubuntuforums.org/showthread.php?t=795525&highlight=surround+sound+pulse](http://ubuntuforums.org/showthread.php?t=795525&highlight=surround+sound+pulse)

seems pulse audio is 2 channel by default, to change it to 5.1...make the edit according to "the easy way" in that link, changing the 2 to a 6 for 5.1 surround. don't forget to uncomment the "default-sample-channels" line (remove the ; at the beginning of the line).

that one edit got all 5.1 channels working for me in both intrepid and jaunty.

hope that helps.

---

### Post by expelledboy on 2009-06-14
> **fooman said:**
> have a look at this guide:

[http://ubuntuforums.org/showthread.php?t=795525&highlight=surround+sound+pulse](http://ubuntuforums.org/showthread.php?t=795525&highlight=surround+sound+pulse)

seems pulse audio is 2 channel by default, to change it to 5.1...make the edit according to "the easy way" in that link, changing the 2 to a 6 for 5.1 surround. don't forget to uncomment the "default-sample-channels" line (remove the ; at the beginning of the line).

that one edit got all 5.1 channels working for me in both intrepid and jaunty.

hope that helps.

hmm.. my surround worked out of the box. Perhaps it is specific to the sound card?

---

