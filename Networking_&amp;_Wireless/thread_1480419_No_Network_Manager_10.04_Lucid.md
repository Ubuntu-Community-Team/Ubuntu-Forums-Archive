---
title: "No Network Manager? 10.04 Lucid"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by jschille on 2010-05-11
EDIT: Solved by RIGHT CLICKING TOP PANNEL --> ADD TO THIS PANEL ---> NOTIFICATION AREA ---> RESTART

_Original Post_
Hmm.. trying to fix my wireless issue (doesn't show any wireless connection or even the option, just states Wired Network) and I have no "Network Manager".

Did 10.04 do away with Network manager?
All I have is 

System->Admin->Network Tools
System->Preferences->Network Connections

```

*-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:f7:92:be
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.6 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:20 memory:f0888000-f0888fff ioport:30d0(size=8) memory:f0889c00-f0889cff memory:f0889800-f088980f
  *-network UNCLAIMED
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f0403fff

```

---

### Post by Iowan on 2010-05-11
Network Manager is still present in 10.04... though there are several threads that mention it missing. It can be added back via the Notification Area... (once again, I'll need to search for a link).

---

### Post by jschille on 2010-05-11
greatly appreciate the help - while i have you here did you notice that my network is "UNCLAIMED"

been trying to find threads to help fix it but haven't come across anything yet.
Is this what is making me not able to see wireless connections?
I have had an ethernet cord plugged into my laptop for over a week now and have to use windows when I leave the house :(

---

### Post by jschille on 2010-05-11
> **Iowan said:**
> Network Manager is still present in 10.04... though there are several threads that mention it missing. It can be added back via the Notification Area... (once again, I'll need to search for a link).

Hey Iowan, I found this thread ::  [http://ubuntuforums.org/showthread.php?t=1469625](http://ubuntuforums.org/showthread.php?t=1469625)

However it did not help me.  First I tried
```


nm-applet --sm-disable

```
That didn't work, this is what I got.
```

jb@jb-laptop:~$ nm-applet --sm-disable
An instance of nm-applet is already running.

** (nm-applet:2081): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

```

another fix stated in the thread was enter the command
```
sudo edit /etc/NetworkManager/nm-system-settings.conf
```
and change managed = false to true.  however when i enter that command i get the following...
```

jb@jb-laptop:~$ sudo edit /etc/NetworkManager/nm-system-settings.conf
Warning: unknown mime-type for "/etc/NetworkManager/nm-system-settings.conf" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"

```

---

### Post by Iowan on 2010-05-11
Try using **nano** or **gedit** for the editor:```
sudo nano /etc/NetworkManager/nm-system-settings.conf
```
or
```
[COLOR="Red"]gksudo[/COLOR] gedit /etc/NetworkManager/nm-system-settings.conf
```
Any luck adding the Notification Area back to the panel?

---

### Post by jschille on 2010-05-11
Yes Iowan! It is back on the panel. Now I just have to get my wireless connections showing again :)

---

### Post by pdc on 2010-05-11
is this of any help to you with your broadcom 4322 ?

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by turbuntu on 2010-05-13
thanks jschille and lowan for the solution.
if this problem arise after a fresh installation, you might just need to reboot the system without any cable connected to your laptop after installing the driver. that's how mine solved on dell vostro with broadcom 4312

---

### Post by alexei.colin on 2010-08-11
I've faced the missing-but-running network manager applet problem when (temporarily) switching from wicd to network-manager. This made the icon appear in the panel:
```
sudo service network-manager stop
sudo service network-manager start
```

---

