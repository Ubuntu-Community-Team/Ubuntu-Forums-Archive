---
title: "Removed network-manager, now no LAN or WLAN. Please help!"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by klopus on 2009-05-30
On my ASUS EeePC 1000HE I'm trying Kubuntu Jaunty. From my current experience with Ubuntu I already knew that stock wireless manager won't connect to WEP unless I switched to Wicd. Same thing repeated in Kubuntu - it sees wireless around me but refuses to connect to my home router with my WEP passphrase.

In Gnome Synaptec happily uninstalled stock manager as part of Wicd installation and everything was fine. Not so with KDE package manager. It refused to install Wicd unless I remove network-manager. Which I did and immediately lost my wired connection (without naturally gaining wireless  Cry ). No rebooting helped. What are my options?

And in general, what's wrong with network managers in [K]Ubuntu? I tried Mandriva and their manager didn't have any problems going wireless.

---

### Post by cariboo on 2009-05-30
Have you tries connecting manually. Open an Applications-->Accessories-->Terminal using gnome or K-->Applications-->Utilities-->TerminaL for kde and type:

```
sudo dhclient eth0
```

for wired, and

```
sudo dhclient wlan0
```

for wireless.

---

### Post by lswb on 2009-05-30
You should be able to connect using the cli tools. For purpose of illustration here lets say that your wired ethernet interface is eth0 and the wireless interface is wlan0

For typical wired connection, in a terminal,
```

sudo ifconfig eth0 up
sudo dhclient eth0

```
should get you going. Wireless is a little trickier. For this example I use a network name of "mynetwork" and a wep key of abcdef0123. For typical wireless network using a router/access point that handles dhcp,

```

sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed iwconfig essid "mynetwork" key abcdef0123
sudo dhclient wlan0

```


I have seen some people recommend this sequence but haven't found it necessary myself:
```

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed essid "mynetwork" key abcdef0123
sudo ifconfig wlan0 up
sudo dhclient wlan0

```


Once you have the network going, you can fire up the package manager and try installing wicd again.

As far as network manager in ubuntu, I found the version in JJ to be superior to earlier efforts but still has some problems. NM in 8.04 clearly was not ready for prime time.

---

### Post by dmizer on 2009-05-30
You could also download and install the old gnome tool for managing your network (on a separate computer of course): [https://launchpad.net/ubuntu/jaunty/lpia/gnome-network-admin/2.22.2-0ubuntu4](https://launchpad.net/ubuntu/jaunty/lpia/gnome-network-admin/2.22.2-0ubuntu4). Then you'll be able to manage your network from system > administration > network

---

### Post by klopus on 2009-05-31
Thanks everybody for advise. Simple 
```
sudo dhclient eth0
```
did the trick and restored wired connection without the need for the Network Manager GUI applet! After that I downloaded WICD which totally did the trick with wireless - just enter your WEP password and reboot. WICD is simply a much better network manager than the stock ones in both Ubuntu and Kubuntu. If WICD was a distro standard then both Ubuntu and Kubuntu would have truly awesome out-of-the-box experience with netbooks like Asus 1000HE (and probably others).

Another lesson learned was that Kubuntu's stock package manager is lacking and buggy compared with Synaptec standard in Ubuntu. Though Synaptec is a GTK app nothing prevents from installing it in Kubuntu. It runs fine, just doesn't look all that good smile

---

