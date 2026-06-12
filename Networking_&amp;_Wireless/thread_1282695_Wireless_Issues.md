---
title: "Wireless Issues"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by bobarrik on 2009-10-04
So I have a Inspiron 1100 and Ubuntu 9.04.

I have been trying to get my Linksys Wireless-G (WPC54 ver. 1.2) to work on this thing for the longest time because my ethernet port is broken.


I have tried the ndiswrapper approach and I think I did it right, but maybe not... I don't know.



Can someone help me get a wifi connection?

---

### Post by Metaljaz on 2009-10-04
You need to find out what chipset the linksys is using. If it is using the broadcom chipset you do not need ndiswrapper, you can use the broadcom 43xx firmware. Try typing lspci in the terminal window and post the results of the network controller line.

---

### Post by darco on 2009-10-04
I just upgraded to Karmic Beta and my wifi was broke..the sticky above helped me....

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

good luck

darco

---

