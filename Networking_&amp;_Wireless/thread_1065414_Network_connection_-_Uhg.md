---
title: "Network connection - Uhg"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by smccosh on 2009-02-09
Hi,  

I installed Ubuntu 8.10 on an IBM ThinkPad 600E.
I can't get it to connect to my Linksys router (wired or wireless).
I've spent most of my time trying to connect with a Cisco Aironet 350 wireless adapter, but I also have a 3Com network adapter.
Both are PC Cards.  As I said I can't get either one to connect.

I've spent a lot of time searching the forums / Internet for help on this problem.

I initialized the laptop bios and turned off "fast boot".

Ubuntu seems to detect the card just fine:
```

sudo pccardctl ident
Socket 1:
product info: "Cisco Systems", "350 Series Wireless LAN Adapter", "", ""
manfid: 0x015f, 0x0000a
function: 6 (network)

```


The lights on the Cisco card are blinking:  
Activity blinks fast
Status blinks slow

The Network Manager has Networking enabled and Wireless enabled.
Network manager shows the essid of my Linksys wireless router, and it shows the signal strength.
I turned off security on my wireless router.

In "Network Connections", I created a new wireless connection
with the SSID=linky, Mode=Infrastructure, MTU=automatic

---

### Post by smccosh on 2009-02-12
Any ideas?


Here is my kernel info:

uname -a

```

Linux s-laptop 2.6.27-7-generic #1 SMP Thu Feb 12 2008 i686 GNU/Linux

```

---

### Post by superprash2003 on 2009-02-12
type **sudo dhclient wifi0 ** .. your wifi0 is connected to the network but isnt getting an ip

---

### Post by smccosh on 2009-02-12
Hi, 

I booted from the CD into a live session and the network card connected with no problem!!!  I used network manager to connect.

I'm re-installing from the live session right now.

Hope it works!

---

### Post by smccosh on 2009-02-12
It worked!  After a re-install from the Live Session, the network is fine!

---

