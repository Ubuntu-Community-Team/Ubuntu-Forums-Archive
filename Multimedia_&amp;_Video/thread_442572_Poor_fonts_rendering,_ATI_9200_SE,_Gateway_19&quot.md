---
title: "Poor fonts rendering, ATI 9200 SE, Gateway 19&quot; WS Monitor"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by zjameria on 2007-05-13
I recently installed Latest Ubuntu on my PC. I have ATI  9200 SE with Gatewy 19" LCD monitor.  I tried installing both FGLRX and open-source drivers from the documented links below:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

I tried both of these drivers. Additionally, I also tried installing drivers with Envy, but it said ATI Legacy drivers dont support my card, eventhough it correctly identified and said it would support.

Currenlty, I have following.

```
zenith@bbl-gbl:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
zenith@bbl-gbl:~$ 

```

```
zenith@bbl-gbl:~$ lspci
(other stuff here)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

```
 
Everything works fine except the display of fonts. Movie rendering is perfect as well. Reading the playlist of xmms media player is almost impossible with current display of fonts. Its also difficult to distinguish between double quotations (" ") and single quotations (' '). Any tips or advice will be greatly appreciated.

Thank you.
Ubuntu Rocks!

---

### Post by killabc on 2007-05-13
Try this tips to resolve your problem.. work for me..

[http://ubuntuforums.org/showthread.php?t=343670&highlight=font+rendering](http://ubuntuforums.org/showthread.php?t=343670&highlight=font+rendering)

---

