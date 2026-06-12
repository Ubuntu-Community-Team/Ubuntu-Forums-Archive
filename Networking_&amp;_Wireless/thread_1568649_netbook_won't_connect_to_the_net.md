---
title: "netbook won't connect to the net"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by shebear on 2010-09-05
I have a HP mini 1030NR that is the solid state 16 gb version.  Windows was taking over all my memory so my son suggested that I switch to a Linux operating system.  I am very impressed but have run into a problem that I can't seem to resolve.

I can't connect to the internet.  After finding these forums, I have been able to determine that the card is disabled.  

this is what I get:

description: wireless interface
physical ID: 1
logical name: wlan0
serial 00:24:2b:bf:49:92
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

I have checked the firefox file and it is set to work online.  When I check to see if the card is enabled, the above is what I get.  When I try moving the physical switch on the netbook, the light stays orange.  

I totally deleted windows on the netbook and am using a different computer to write this.  I am also computer illiterate, so please write slowly so I will understand. ;)

---

### Post by Iowan on 2010-09-05
Right-click the Network Manager icon and verify Networking and Wireless are enabled. Otherwise, one of these links might be helpful:
[http://ubuntuforums.org/showthread.php?t=1564615]("http://ubuntuforums.org/showthread.php?t=1564615")
[http://ubuntuforums.org/showthread.php?t=1484913]("http://ubuntuforums.org/showthread.php?t=1484913")
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")

---

### Post by shebear on 2010-09-06
I tried all that you suggested and nothing helped.  I still get that the network card is disabled and when I try to manually turn it on with the switch, nothing happens.  The light stays orange indicating it is off.

Is there another way to enable the network card other than the physical switch?

---

### Post by shebear on 2010-09-24
Still can't get my wireless card to work.  Any help would be appreciated.

---

### Post by Iowan on 2010-09-24
Wireless isn't my forte, but you can check **rfkill list** to see if something has it blocked. I presume you've right-clicked on Network Manager icon and verified Wireless is enabled.

---

