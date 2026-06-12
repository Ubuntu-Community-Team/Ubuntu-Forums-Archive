---
title: "Wireless worked once and no idea how to get it back"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by mr_gourami on 2009-04-07
So the first time i tried to use the wireless was in hong kong airport. didnt work. Until i plugged into the 24 free internet bar with a cable. then a window poped up and let me install some sort of special driver for the wireless card. hey it works!

now i am home and wireless is gone. when i right click on the network icon there is not even an option for 'enable wireless' only 'enable networking'... its as if the computer doesnt even realize that there is a wireless device in the computer..

i did the   lshw -C network

*-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:59:64:d4:92:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

so what this means i dont know. and i looked under the driver thing, no its not even an option now to activate or deactivate the wirless driver. Any help would really be nice.

---

### Post by Sam Lars on 2009-04-09
Did your wireless work "out of the box?"
Also, could you post the output of
```
lspci | grep Network
```

---

