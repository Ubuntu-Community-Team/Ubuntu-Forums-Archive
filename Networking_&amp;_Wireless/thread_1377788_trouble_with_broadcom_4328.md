---
title: "trouble with broadcom 4328"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by chuckmurphy on 2010-01-10
I've tried working through a couple of threads to solve this and no luck so far. I've tried to install the wl driver without success.
> 
lspci | grep Broadcom
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

results from *lshw -c network*
> chuck@chuck-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:91:ad:13
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.101 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:23:19:e8:a3:0b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

results from lsmod
> lsmod |grep -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
wl                   1281364  0 
ieee80211_crypt        13444  1 wl
ssb                    41220  1 b44

In the Hardware drivers, the Broadcom STA wireless driver shows that it is active. But the wireless card acts like it isn't on. Not sure what to do next.

---

### Post by chuckmurphy on 2010-01-10
If it helps, I'm running Jaunty on a Dell 1700 Vostro.

---

### Post by chuckmurphy on 2010-01-10
bump for help

---

### Post by lidex on 2010-01-10
How about this one?
[http://ubuntuforums.org/showthread.php?p=8539988#post8539988]("http://ubuntuforums.org/showthread.php?p=8539988#post8539988")

---

### Post by chuckmurphy on 2010-01-21
Okay, I've gotten the wl driver installed, but every time I reboot, the ssb driver starts first and interferes with wl. In order to make it work, I've got to hit the terminal and use the following commands:
> chuck@chuck-laptop:~$ sudo rmmod b44
[sudo] password for chuck: 
chuck@chuck-laptop:~$ sudo rmmod ssb
chuck@chuck-laptop:~$ sudo rmmod wl
chuck@chuck-laptop:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
chuck@chuck-laptop:~$ sudo depmodWhat boot up file and what code do I need to add to make this automatic? Also, if I need wired internet, do I just restart b44? I'm not sure if b44 is dependent on ssb.

---

### Post by bkratz on 2010-01-22
> **chuckmurphy said:**
> Okay, I've gotten the wl driver installed, but every time I reboot, the ssb driver starts first and interferes with wl. In order to make it work, I've got to hit the terminal and use the following commands:
What boot up file and what code do I need to add to make this automatic? Also, if I need wired internet, do I just restart b44? I'm not sure if b44 is dependent on ssb.

found an old Chili post where he mentioned where the file should be put. Hopefully this will help.   Remember this was for a different card! It is just to show you where it goes.

[http://ubuntuforums.org/showpost.php?p=8342691&postcount=17](http://ubuntuforums.org/showpost.php?p=8342691&postcount=17)

---

### Post by lidex on 2010-01-22
I believe you need to "blacklist" the unwanted driver:
[http://ubuntuforums.org/showthread.php?t=796831]("http://ubuntuforums.org/showthread.php?t=796831")

On this page scroll down to "(3) Configuration":
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by pdc on 2010-01-22
I am sure lidex is right;

if you wanted to look at running this diagnostic script

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English)

it provides analysis and suggestions; it is likely also to point you are running ndiswrapper and a broadcom?

---

