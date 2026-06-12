---
title: "Two nics at the same time"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by MaindotC on 2009-08-15
I have two machines and I'd like to use the wired interface to transfer files from one machine to another, but I'd like to keep the wireless interfaces active to connect to my access point.  That's really my question, but I'm sure you'd want to know why so I'll post the reasoning below, otherwise read no further.

I use wireless from my landlord so the AP isn't in my residence.  I like to stream dvd's or tv shows to my friends using Webcamstudio + uStream or Livestream.  I have two machines, and one is faster than the other.  The slower machine runs all my services that I don't want interrupted - like apache, sftpd, sshd, etc.  So, when I have movies to watch I like to keep them on that machine.  However, sometimes I need the faster machine to do this.  So, when I need to transfer a movie file from one machine to the other, it's really slow going through my unsupported wireless card that gets 24 mb/s, through my landlord's AP, and back to the other machine also using an unsupported wireless card running 24 mb/s.  They're right next to each other, so I'd like to just use the wired interface to beam that file right across.  The difference is literally like 2 minutes versus an hour.  To do this, I need to select "Wired Network" in nm-applet, and then assign it an ip address (on both machines).

Again, I want to keep the wireless interfaces up for accessing the internet, but I want the wire to transfer files between machines without taking down the wireless interface.

---

### Post by Iowan on 2009-08-15
Assuming the second machine doesn't need Internet access...
NM will (apparently) manage only one connection at a time, so the "other" connection will need to be set up in */etc/network/interfaces*. A static address (different subnet than wireless) might be easiest. Use **route** to set up a path to the second machine through the proper interface.

---

### Post by eldragon on 2009-08-15
if its just a temporary connection, then using ifconfig is all you need

```

# ifconfig <iface> ip

```

that would automagically set the netmask and route entry too.

im using a small script that effectively turns my notebook into a NAT (shares internet comming from the wlan adapter through my eth0 adapter). the script looks like this:

```

#!/bin/bash

ifconfig eth0 up
ifconfig eth0 192.168.11.1
iptables --table nat --append POSTROUTING --out-interface wlan0 -j MASQUERADE
iptables --append FORWARD --in-interface eth0 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward

```

then you need to setup your other computer in the 192.168.11.0 range and set as a default gw your internet access point (in my case, 192.168.10.1)


the connection link looks like this:
[internet]----[wireless router] * * * * * [wlan adapter notebook]--[eth0 adapter notebook] ----- [wired computer2  adapter]

---

### Post by MaindotC on 2009-08-15
Well, yeah I'd like both machine's wireless interfaces to remain up thus maintaining internet access.  I'll check out the man pages for those items you suggested.

---

### Post by MaindotC on 2009-08-15
> **eldragon said:**
> if its just a temporary connection, then using ifconfig is all you need

```

# ifconfig <iface> ip

```


Hah kickass that works!  Yeah a temp connection is all I really need.  Thanks a bunch!

---

