---
title: "wlan0 &lt;=&gt; eth0 bridge"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by tylerwagler on 2010-09-25
Ok, here is what I'm going for.  My friend two houses down has an internet connection that I'm paying half for.  He has a wireless router that I have an OK signal on.  I'm setting up an ubuntu 10.04 server with a USB wifi adapter to connect to his network.  I'd like to bridge that connection to the eth0 and take that to a switch and hard wire the rest of my computers and have them obtain an IP from the router.  I've already given up on wpa_supplicant and changed it to WEP and I can now connect and access the internet.  The only problem I have is that I lose connectivity when i set up br0 by doing bridge_ports eth0 wlan0.  It's a 192.168.0.x network and I'm setting up a static IP for the bridge.  Any ideas or help would be wonderful.

---

### Post by BkkBonanza on 2010-09-25
You should be able to make that work. 
What are the exact commands you've done so far?

Maybe post output of **brctl show**.

You likely need to add an ip address and routes if you intend to use the same machine for anything but a bridge.

---

### Post by tylerwagler on 2010-10-07
ok, I have the wpa_supplicant working now.  I just need to know how to configure my /etc/networking/interfaces file so that it calls wpa_supplicant and waits about 15 seconds, then statically assigns br0 to a specific IP, and finally bridges the ports.

---

### Post by BkkBonanza on 2010-10-07
The simplest is to add a script to the /etc/network/if-up.d/ directory. It gets called when an interface is brought up and is given two environment variables you can test.

$IFACE contains the interface being brought up
$MODE contains the mode which is set to "start" when being brought up

So you can have a script along this lines...

```

#!/bin/bash

if [ "$IFACE" = "eth0" ] && [ "$MODE" = start ]; then
  wpa_supplicant call here...
  sleep 15
  bridge call here...
fi
```

---

### Post by tylerwagler on 2010-10-07
even manually doing each step and waiting for wpa_supplicant, the bridge doesn't work.  I'm trying iptables now, but I'm not having the best of luck.

---

### Post by louism873 on 2010-10-18
I have got it working.
My method:
System -> Preferences -> network connections -> eth0 -> edit (right hand side) -> IPv4 -> method:shared to other computers.
i hope this works for you.:)

---

### Post by gelimeri on 2010-10-19
Hi, I have the same problem with an *Intel Corporation PRO/Wireless 3945ABG [Golan]*. No network manager running, in a root terminal:
```

brctl addbr br0
wpa_supplicant -B -bbr0 -iwlan0 -c wpa_supplicant.conf
brctl addif br0 wlan0

```
And ```
dhclient
``` doesn't work neither for br0 nor for wlan0.
May someone help me?
Thanks

---

