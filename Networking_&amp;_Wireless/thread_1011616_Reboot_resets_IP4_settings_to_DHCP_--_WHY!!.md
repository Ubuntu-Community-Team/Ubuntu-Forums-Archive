---
title: "Reboot resets IP4 settings to DHCP -- WHY?!!"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by BobSutan on 2008-12-14
Title says it all. So how do I fix it so when I reboot I don't have to reset the IP address, netmask, gateway, and DNS?

---

### Post by BobSutan on 2008-12-15
bump

---

### Post by ThaddeusW on 2008-12-16
> **BobSutan said:**
> Title says it all. So how do I fix it so when I reboot I don't have to reset the IP address, netmask, gateway, and DNS?

I assume you want to use a static ip correct? If you have only one network adapter eth0 is your device name. type ifconfig into a terminal and hit enter. you should only see eth0 and lo (loop back). 

break open a terminal and type in:

```
sudo gedit /etc/network/interfaces
```

You then need to edit the entry for eth0. My static interfaces file  looks like this: 
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0


I don't know for sure if you need the "auto eth0" at the end though.

You should then bring down the interface:
```

sudo ifdown eth0

```
Restart networking:
```

sudo /etc/init.d/networking restart

```
Then finally bring the interface back up:
```

sudo ifup eth0

```

 That or just reboot.

---

### Post by iponeverything on 2008-12-16
> **BobSutan said:**
> Title says it all. So how do I fix it so when I reboot I don't have to reset the IP address, netmask, gateway, and DNS?

You're very short on details --

What version  8.04? -- 8.10? -- Network Manager? -  WICD? - Manual Configuration?   Anything else that *you* can think of that might be relevant?

---

### Post by BobSutan on 2008-12-16
8.10
Manual configuration
Static IP4 Address

---

### Post by Iowan on 2008-12-16
Dunno if it'll help, but there is a [workaround]("http://ubuntuforums.org/showthread.php?t=974382") for static IP assignment.

---

### Post by BobSutan on 2008-12-16
> **Iowan said:**
> Dunno if it'll help, but there is a [workaround]("http://ubuntuforums.org/showthread.php?t=974382") for static IP assignment.

Thanks. I gave singingstars recommendation a shot and it worked!

[http://ubuntuforums.org/showpost.php?p=6159551&postcount=3](http://ubuntuforums.org/showpost.php?p=6159551&postcount=3)

---

### Post by The Cog on 2008-12-17
I recommend wicd [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/). I couldn't make their install instructions work in synaptic for some reason, so I downloaded the .deb file from [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573) and double-clicked that file to install it.

I like the fact that it has profiles for the wired interface so you can change settings easily.

---

