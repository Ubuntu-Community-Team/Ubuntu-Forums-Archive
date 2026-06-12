---
title: "Point to Point Tunneling Server Connection Errors"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by doctorzeus on 2011-03-28
Hi I recently installed the pptpd server on my system and set it up according to these instructions:
[HTML]
http://forums.bit-tech.net/showthread.php?t=132029[/HTML]

However after setting everything up on attempting to connect to it from a windows machine (windows 7 home premium to be specific) it gives me two errors which are 720 and 800...

It reaches "registering your computer on the network" fine and then gives 720 on the first attempt to connect and then 800 on the second attempt to connect...and then on the third 720 and 4th 800 and so on..

My system running the server's I.P is 192.168.1.70
My system running the windows OS trying to connects I.P is: 192.168.1.66

Can anyone please help me with this? I really want to set up a VPN server :(

---

### Post by doctorzeus on 2011-03-29
Anyone know??

---

### Post by doctorzeus on 2011-03-31
OK found the problem, there was data encryption incompatibilities, disabled/enabled some and it works fine now...

---

