---
title: "lost desktop, left with tty only, need to connect internet to get back"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by kindahero on 2009-06-14
I was trying to get my sound card working. In the process (followed a how-to guide) i removed alsa drivers and reistalled, used the following commands..

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

upto that point, every thing was okay. when i restarted the system expecting to get sounds working, lost the desktop-environment:(:(:(, left with only tty. 
so I hope if i could install ubuntu-desktop again I may get my atleast desktop-environment back.

The worst part is, I am no longer connected with the internet to give apt-get command..

mine is static connection (in the university).. 
previously I established connection with network-manager,( not with /etc/network/interfaces)
now i tried to fill up ips in /etc/network/interfaces and restarted the network.. did not help.. 

Is there anything i should look at.?

using 8.10 , 64 bit
googled around whole night, nothing worked.

plz help me to get back my internet.?

---

### Post by mhgsys on 2009-06-14
Although I really don't understand this has anything to to with your sound drivers:

in tty type

```

 sudo dpkg-reconfigure xserver-xorg

```

then type:

```

sudo /etc/init.d/gdm restart

```

this hopefully will get your desktop back.

---

### Post by kindahero on 2009-06-14
thanks for the reply,, did not help

there is not gdm command itself ... it is saying..

sudo: /etc/init.d/gdm: command not found

BTW , i followed the following guide for troubleshoot my sound
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by kindahero on 2009-06-15
ohh my goodness.. my eth0 was up.. i did not know that..

I am able to connect my computer from outside the university (with ssh)..
it seems to my system incoming connections are okay.. but out going connections are not being resolved..

```

yagnesh@mysys:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:e3:88:9e  
          inet addr:***.**.***.***  Bcast:***.**.***.***  Mask:255.255.252.0
          inet6 addr: fec0::8:216:76ff:fee3:889e/64 Scope:Site
          inet6 addr: 2002:8557:d828:8:216:76ff:fee3:889e/64 Scope:Global
          inet6 addr: fe80::216:76ff:fee3:889e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:264753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:877 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:32290461 (32.2 MB)  TX bytes:223585 (223.5 KB)
          Memory:92200000-92220000 

```

when i say..
```

yag@**$ ping www.google.com
ping: unknown host www.google.com
```


is it problem with any kind of firewall used in my system.?

hope my question is clear.

Thanks..

---

### Post by dmizer on 2009-06-15
To check for firewall:
```
sudo iptables -L
```

For future reference, please take the time to look at the dates of posts. The howto you followed was from 2006. A LOT has happened with linux sound since then.

The package "linux-sound-base" depends on the gnome-desktop. By removing that package you probably removed your entire GUI. To restore your desktop, do **_one_** the following (depending on what environment you had before following the howto):

For Ubuntu (gnome)
```
sudo apt-get install ubuntu-desktop
```
For Kubuntu (KDE)
```
sudo apt-get install kubuntu-desktop
```
For Xubuntu (XFCE4)
```
sudo apt-get install xubuntu-desktop
```

---

