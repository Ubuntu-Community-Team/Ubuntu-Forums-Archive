---
title: "Linksys WUSB54G problems."
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by daxbriggs on 2010-12-14
Hello, I'm very new to Linux, and I have a Linksys Wireless-G USB Network Adapter, 
2.4 GHz, 802.11g. 

It hooks up through USB plug, and when I originally plugged it in I got the message that ubuntu didn't support the drivers, but haven't seen it since. 

I'm hooked up to a LAN cable right now, and can't seem to figure out how to hook up through wireless with this device.  Or I just don't know how.  

When I click on the network connections button on the top right corner (the two computers)  

I can see my Wired Internet, but no wireless. 

When I type lsusb in a terminal I get : (sorry I don't know how to do code blocks)

{
Bus 004 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1915:2234 Linksys WUSB54G 802.11g Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
}

So it is recognizing that it's there, but maybe I just don't know how to use it. 

Also, I'm running Ubuntu Release 10.04 (lucid)

Any help would be nice.  Remember, super new to Linux here.

---

### Post by bkratz on 2010-12-14
Here is a another recent thread about getting that device to work with ndiswrapper, please note that the drivers available from the site mentioned are for 32 bit systems only. Just read it and see what you think.

[http://gutsywww.ubuntuforums.org/showthread.php?t=1615175](http://gutsywww.ubuntuforums.org/showthread.php?t=1615175)

---

