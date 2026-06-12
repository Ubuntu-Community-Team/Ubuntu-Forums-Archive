---
title: "3G Mobile Broadband SOMETIMES Connects"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by ad libitum on 2011-03-21
Hi, I'm using **Ubuntu 10.10** with all the latest updates, it runs great and I'm really pleased with it. 

I've been having some trouble with my **movistar ZTE MF110 3g dongle** though: everything seems to work fine, it's recognized automatically, I've configured the connection with the Network Manager, and I successfully connect to the internet every day. But for some reason about 75% of the time it can't connect! 

When I click on the movistar broadband connection in the network manager, it tries and tries but cannot connect. The only cure that I've found is to give it some time, unplug the dongle, plug it back in, and try again. Or, restart the computer and try it all again. Eventually it works.

It's not really a long-term solution though, as sometimes I don't have 30 minutes to spend faffing about with my dongle. I'm convinced it's a Linux problem, as both my Windows and Mac Os's located in the same room connect with a strong signal every time. 

Has anyone else encountered this problem? I'd really like to be able to count on my Ubuntu computer, but as it stands at the moment I always need a Windows or Mac OS at hand in case Ubuntu can't manage to connect (like right now!)

---

### Post by alexfish on 2011-03-21
hi

can post the results of lsusb command from the terminal
```
lsusb
```and contents of usb_modeswitch.d/files
```
ls /etc/usb_modeswitch.d/*
```

---

### Post by ad libitum on 2011-03-21
```
user@computer:~$ lsusb
Bus 002 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 19d2:0124 ONDA Communication S.p.A. 
Bus 001 Device 004: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@computer:~$ ls /etc/usb_modeswitch.d/*
/etc/usb_modeswitch.d/0421:060c
/etc/usb_modeswitch.d/0421:0610
/etc/usb_modeswitch.d/0471:1210
/etc/usb_modeswitch.d/0471:1237
/etc/usb_modeswitch.d/0482:024d
/etc/usb_modeswitch.d/04e8:689a
/etc/usb_modeswitch.d/04e8:f000
/etc/usb_modeswitch.d/057c:84ff
/etc/usb_modeswitch.d/05c6:1000:sVe=Option
/etc/usb_modeswitch.d/05c6:1000:uMa=AnyDATA
/etc/usb_modeswitch.d/05c6:1000:uMa=Option
/etc/usb_modeswitch.d/05c6:1000:uMa=SAMSUNG
/etc/usb_modeswitch.d/05c6:1000:uMa=Vertex
/etc/usb_modeswitch.d/05c6:2001
/etc/usb_modeswitch.d/05c6:f000
/etc/usb_modeswitch.d/072f:100d
/etc/usb_modeswitch.d/0930:0d46
/etc/usb_modeswitch.d/0ace:2011
/etc/usb_modeswitch.d/0ace:20ff
/etc/usb_modeswitch.d/0af0:6711
/etc/usb_modeswitch.d/0af0:6731
/etc/usb_modeswitch.d/0af0:6751
/etc/usb_modeswitch.d/0af0:6771
/etc/usb_modeswitch.d/0af0:6791
/etc/usb_modeswitch.d/0af0:6811
/etc/usb_modeswitch.d/0af0:6911
/etc/usb_modeswitch.d/0af0:6951
/etc/usb_modeswitch.d/0af0:6971
/etc/usb_modeswitch.d/0af0:7011
/etc/usb_modeswitch.d/0af0:7031
/etc/usb_modeswitch.d/0af0:7051
/etc/usb_modeswitch.d/0af0:7071
/etc/usb_modeswitch.d/0af0:7111
/etc/usb_modeswitch.d/0af0:7211
/etc/usb_modeswitch.d/0af0:7251
/etc/usb_modeswitch.d/0af0:7271
/etc/usb_modeswitch.d/0af0:7301
/etc/usb_modeswitch.d/0af0:7311
/etc/usb_modeswitch.d/0af0:7361
/etc/usb_modeswitch.d/0af0:7381
/etc/usb_modeswitch.d/0af0:7401
/etc/usb_modeswitch.d/0af0:7501
/etc/usb_modeswitch.d/0af0:7601
/etc/usb_modeswitch.d/0af0:7701
/etc/usb_modeswitch.d/0af0:7801
/etc/usb_modeswitch.d/0af0:7901
/etc/usb_modeswitch.d/0af0:8200
/etc/usb_modeswitch.d/0af0:8201
/etc/usb_modeswitch.d/0af0:8300
/etc/usb_modeswitch.d/0af0:8302
/etc/usb_modeswitch.d/0af0:8304
/etc/usb_modeswitch.d/0af0:8400
/etc/usb_modeswitch.d/0af0:c031
/etc/usb_modeswitch.d/0af0:c100
/etc/usb_modeswitch.d/0af0:d013
/etc/usb_modeswitch.d/0af0:d031
/etc/usb_modeswitch.d/0af0:d033
/etc/usb_modeswitch.d/0af0:d035
/etc/usb_modeswitch.d/0af0:d055
/etc/usb_modeswitch.d/0af0:d057
/etc/usb_modeswitch.d/0af0:d058
/etc/usb_modeswitch.d/0af0:d155
/etc/usb_modeswitch.d/0af0:d157
/etc/usb_modeswitch.d/0af0:d255
/etc/usb_modeswitch.d/0af0:d257
/etc/usb_modeswitch.d/0af0:d357
/etc/usb_modeswitch.d/0b3c:c700
/etc/usb_modeswitch.d/0b3c:f000
/etc/usb_modeswitch.d/0cf3:20ff
/etc/usb_modeswitch.d/0fce:d0cf
/etc/usb_modeswitch.d/0fce:d0e1
/etc/usb_modeswitch.d/0fce:d103
/etc/usb_modeswitch.d/1004:1000
/etc/usb_modeswitch.d/1004:607f
/etc/usb_modeswitch.d/1004:613a
/etc/usb_modeswitch.d/1004:613f
/etc/usb_modeswitch.d/1033:0035
/etc/usb_modeswitch.d/106c:3b03
/etc/usb_modeswitch.d/106c:3b06
/etc/usb_modeswitch.d/1076:7f40
/etc/usb_modeswitch.d/1199:0fff
/etc/usb_modeswitch.d/1266:1000
/etc/usb_modeswitch.d/12d1:1001
/etc/usb_modeswitch.d/12d1:1003
/etc/usb_modeswitch.d/12d1:101e
/etc/usb_modeswitch.d/12d1:1031
/etc/usb_modeswitch.d/12d1:1414
/etc/usb_modeswitch.d/12d1:1446
/etc/usb_modeswitch.d/12d1:14ad
/etc/usb_modeswitch.d/12d1:14c1
/etc/usb_modeswitch.d/12d1:1520
/etc/usb_modeswitch.d/12d1:1521
/etc/usb_modeswitch.d/12d1:1523
/etc/usb_modeswitch.d/12d1:1557
/etc/usb_modeswitch.d/1410:5010
/etc/usb_modeswitch.d/1410:5020
/etc/usb_modeswitch.d/1410:5030
/etc/usb_modeswitch.d/1410:5031
/etc/usb_modeswitch.d/1410:5041
/etc/usb_modeswitch.d/148f:2578
/etc/usb_modeswitch.d/16d8:6803
/etc/usb_modeswitch.d/16d8:6803:?
/etc/usb_modeswitch.d/16d8:700a
/etc/usb_modeswitch.d/16d8:f000
/etc/usb_modeswitch.d/198f:bccd
/etc/usb_modeswitch.d/19d2:0003
/etc/usb_modeswitch.d/19d2:0026
/etc/usb_modeswitch.d/19d2:0040
/etc/usb_modeswitch.d/19d2:0053
/etc/usb_modeswitch.d/19d2:0083
/etc/usb_modeswitch.d/19d2:0101
/etc/usb_modeswitch.d/19d2:0103
/etc/usb_modeswitch.d/19d2:0115
/etc/usb_modeswitch.d/19d2:1001
/etc/usb_modeswitch.d/19d2:1007
/etc/usb_modeswitch.d/19d2:1009
/etc/usb_modeswitch.d/19d2:1013
/etc/usb_modeswitch.d/19d2:2000
/etc/usb_modeswitch.d/19d2:fff5
/etc/usb_modeswitch.d/19d2:fff6
/etc/usb_modeswitch.d/1a8d:1000
/etc/usb_modeswitch.d/1a8d:1000:uPr=5G
/etc/usb_modeswitch.d/1ab7:5700
/etc/usb_modeswitch.d/1b7d:0700
/etc/usb_modeswitch.d/1bbb:f000
/etc/usb_modeswitch.d/1c9e:1001
/etc/usb_modeswitch.d/1c9e:9200
/etc/usb_modeswitch.d/1c9e:9e00
/etc/usb_modeswitch.d/1c9e:f000
/etc/usb_modeswitch.d/1dd6:1000
/etc/usb_modeswitch.d/1e0e:f000
/etc/usb_modeswitch.d/1ee8:0009
/etc/usb_modeswitch.d/1ee8:0013
/etc/usb_modeswitch.d/1f28:0021
/etc/usb_modeswitch.d/1fac:0130
user@computer:~$ 
```

---

### Post by alexfish on 2011-03-21
hi

from the info, most seems to be fine , so just wondering if there is a problem with modem-manager(zte plugins),as from the id's the device is a zte mf110 Variant (may be a resent device),
or if the device is looping back on the tty's (possible due to ongoing refinements at kernel level)

first thoughts, could it be the modem-manager hanging on to the device and can't recognise that it is doing so, hence (give it time) = it can't connect as it is locking the ports,(possible due pre-probing the modem , or a failure on the first attempt to connect or if there has been a [COLOR=Blue]disconnection after a successful connection[/COLOR]), the part highlighted in blue , could give an indication , Does this also happen.

suggest try ppp or wvdial ( wvdial is not installed at default) see if there is any improvement

can read through this how to as regards alternate methods of connections,

[How To : Mobile Broadband Connections [ Ubuntu  10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

if you have any queries or if still can't get a stable connection can post back here,

regards

alexfish

---

### Post by ad libitum on 2011-03-22
Okay, I have installed a newer kernel (2.6.38 generic) and now everything is working fine! I guess whatever the problem was got sorted out in the update.

Thanks for the help! :popcorn:

---

