---
title: "Network manager icon in 9.10"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by RalphS on 2009-11-03
Upgraded to 9.10, now instead of the 2 screens network manager displays an Ethernet port with a disconnected cable.

Network is eth0, managed by network manager but manually configured, works fine. If I yank the cable it displays the 2 screens and a red X.  

ralph@ralph-desktop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

ralph@ralph-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:56:bd:48  
          inet addr:192.168.1.151  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe56:bd48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11950341 (11.9 MB)  TX bytes:1463163 (1.4 MB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

EDIT: After updating /etc/NetworkManager/nm-system-settings.conf to managed = true (not sure why it was false), I now instead have a butt-ugly huge *** black Ethernet port icon, slightly better I guess...

---

### Post by lotuseclat79 on 2009-11-03
Hi RalphS,

My /etc/network/interfaces file is:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

I have a Verizon FiOS account and usually just work from a Live CD from home, but I have a need to get a new ip address every time I connect to the Internet (DHCP usually takes care of that).  You might just try adding those two statements to yours to see if it improves your situation and keep it there anyway since you do have ethernet.

Yeah, butt-ugly indeed! LoL!

-- Tom

---

### Post by i22yb on 2009-11-03
I think the point he is trying to make, that I've noticed also, is that the icon for a connected WIRED network looks like a disconnected symbol.  It's a bit confusing.  The connected symbol should be a plugged in icon, not an unplugged one.

---

### Post by veko on 2009-11-11
> **i22yb said:**
> I think the point he is trying to make, that I've noticed also, is that the icon for a connected WIRED network looks like a disconnected symbol.  It's a bit confusing.  The connected symbol should be a plugged in icon, not an unplugged one.

My words, exactly. I spent some time myself  trying to figure out why Network manager shows disconnected icon, before I realized that the actual disconnected icon is two computers and a red cross over them. So apparently that "cord not plugged in" -icon is indeed means connected wired network.

To add confusion, I don't understand why the icon changes to completely different one when network is disconnected. Common logic would suggest them to follow the same theme and to show connected/disconnected cord  or two computers without/with cross over them.

Does anyone know if these are external icons and if so, where they are stored? I 'd like to change them manually to something more illustrative ones.

---

### Post by SawyerLX on 2009-11-18
terminal:
  sudo pppoeconf

The broken network manager applet, could be fixed in the next few updates.
9.10 Final: Ubuntu Broken Linux.
 I'm gonna wait to see what happens!

---

### Post by abean on 2009-11-18
I uninstalled it as I don't need it, I know how to use the terminal for that type of thing.

to get rid of it all together and rely on ur m4d sk1llz

sudo apt-get remove network-manager network-manager-gnome

Cheers

Abe

---

### Post by tc7 on 2010-05-03
This still appears to be an issue in Lucid (10.04).

NetworkManager works fine, but icon shows disconnected cable when physically connected and working.
Icon (correctly?) changes to red cross / old disconnected icon when cable is unplugged.

:confused:

---

