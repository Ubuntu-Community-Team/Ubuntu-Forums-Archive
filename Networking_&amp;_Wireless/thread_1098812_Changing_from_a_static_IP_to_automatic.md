---
title: "Changing from a static IP to automatic?"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by Schendje on 2009-03-17
Hi everyone,

I've got a fairly regular desktop here, running Ubuntu 8.10 since it was released. I upgraded from 8.04.

It was working great until I moved: in my new apartment I can't connect to the network/Internet. I believe the problem is that I used to have a static IP, but now I have a router with automatic IP (DCHP I think?).

I'm using a simple wired connection. When I right-click on the Networking Manager icon on the taskbar and choose "Properties", it tells me my static IP, but I can't change it in this window. I tried to fix it through the "new" Network Configuration, but it didn't work. I also tried to edit /etc/network/interfaces, but no success there either. I tried several terminal commands (like "ifconfig eth0 up" or "ifocnfig -a") but they also didn't help.

I know it's not the router, and I doubt it's the hardware.

Here's some more information:

/etc/networking/interfaces:

```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.178.102
netmask 255.255.255.0
gateway 192.168.178.1

auto eth0
```

From lspci:

```
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
```

Hope someone can help me and I didn't miss a topic during my search!

---

### Post by thehouseofho on 2009-03-17
When you edit your eth0 connection, there should be a tab that read IPv4 Settings.  Click on that tab and select Automatic from the Method drop-down menu.

---

### Post by feelshift on 2009-03-17
System -> Preferences -> Network Configuration -> "Edit Connections", select your device then click "Edit" -> the "IPv4 Settings" tab and then change the "Method" from "Manual" to "Automatic (DHCP)" or whatever. ;)

---

### Post by Schendje on 2009-03-17
Thanks for the quick replies! :)

Unfortunately, I already tried this... I even added a new connection and filled out the MAC address. I put it on Automatic.

Yet this didn't work? I only have one connection in "Network Connections".

---

### Post by Iowan on 2009-03-17
Have you tried commenting out the definition for eth0?
```
auto lo
iface lo inet loopback

;iface eth0 inet static
;address 192.168.178.102
;netmask 255.255.255.0
;gateway 192.168.178.1

;auto eth0
```(Remember to restart networking afterwards).

---

### Post by Schendje on 2009-03-17
Yes, that worked! :o

I tried to do that, but forgot to comment the last line, "auto eth0"... Not very smart, but I'm learning! :D

Thanks!

---

