---
title: "repository error: Asus netbook"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by redcrystalmoon on 2010-02-07
Hello, I have been trying to get my wireless working with ndiswraapper unsuccessfully so I'm just going to upgrade to the next distro. 
My wifi was working fine until I updated my system (asus netbook, Model # zg5, atheros AR242x wifi card)
I'm currently running eeebuntu 9.04.
When I went to the update manager I was originally told there was an upgrade to 9.10 available but I didn't install it I went with all the recommended updates instead and now the new kernel wont recognize my wifi card.

So I've decided to just do the upgrade and see if the problem is fixed then. But now when I go into update manager there's no option available for a new upgrade. I'd really like to just do it that way if possibly instead of having to download the ISO and completely reinstall everything.
When I check the updates I get this error:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81D820A9BB7A1A83Failed to fetch [http://www.statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages](http://www.statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://repos.eeebuntu.org/dists/intrepid/main/binary-i386/Packages](http://repos.eeebuntu.org/dists/intrepid/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://repos.eeebuntu.org/dists/intrepid/non-free/binary-i386/Packages](http://repos.eeebuntu.org/dists/intrepid/non-free/binary-i386/Packages)  404 Not Found
Failed to fetch [http://repos.eeebuntu.org/dists/intrepid/contrib/binary-i386/Packages](http://repos.eeebuntu.org/dists/intrepid/contrib/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

When I was following the tutorial for ndiswrapper it says to make sure my multiverse and univers repositories were enabled but in the software sources list, there are no multiverse or universe there, also there seems to be a bug because the little white boxes arn't showing a checkmark when I click on them... 
The repositories that are available to me are: 
 
EEEbuntu software:
Downlaodable fro mthe internet
Officially supported (main)
DFSG-compatable software with Non-Free Dependencies (contrib)
Non-DFSG-compatable software (non-free)

Download from: Main server

And a whole bunch in third party software.

So, my question is: Does anyone know how to get the little button back that allows me to upgrade my distro right from the update manager, or at least how I can upgrade without having to completely reinstall everything??

Thanks a lot to anyone who can shed any light on this for me...

---

### Post by redcrystalmoon on 2010-02-07
OR:
If anyone decides they want to give me a hand with getting ndiswrapper working then by all means fire away some answers, or questions... here's some outputs that may be helpful... I've been trying to follow tutorials but I'm getting stuck...

I can be a fast learner though! with the right direction! I'm kind of a newb but I would like to know how to figure this shtuff out...

louise@louise-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
04:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

louise@louise-laptop:~$ uname -m
i686

louise@louise-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netathw : driver installed
    device (168C:001C) present (alternate driver: ath5k)
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netathwx : driver installed
    device (168C:001C) present (alternate driver: ath5k)

I have downloaded a driver, maybe it's not the right one... any tips on how to find the right driver?
When I install it through the ndis gui here's what comes up:
unable to see if hardware is present
netathw hardware present: yes
netathwx hardware prestent: yes

I've blacklisted these:
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklistas well as: ath_pci & ath_hal

apparently I can find the appropriate drivers at this website:
[http://www.burnthesorbonne.com/?page_id=32](http://www.burnthesorbonne.com/?page_id=32)
according to the "comprehensive ndiswrapper guide" at the beginning of the threads, but when I type in my chipset id to the search I get this page:
[http://www.burnthesorbonne.com/?page_id=39](http://www.burnthesorbonne.com/?page_id=39)
and the highlighted numbers still don't match up to mine, and I don't see where I can get them from...
 
the one I downloaded was from the asus website but I don't know if I'm supposed to download the same one I have or just one that has a similar chipset ID??

here's something else that might help:
louise@louise-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:59:33:05
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.14 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

lsmod | grep ndis ... returns nothing, and when I run: sudo modprobe ndiswrapper
i GET THIS:
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.


Anyone?? Please?!

---

### Post by redcrystalmoon on 2010-02-08
bump

---

### Post by snowpine on 2010-02-08
Hi r.c.m., I would imagine this error has something to do with the major changes over at eeebuntu (eeebuntu is not Ubuntu). As you probably know, they are switching the entire eeebuntu project from Ubuntu to Debian: [http://www.eeebuntu.org/](http://www.eeebuntu.org/)

I would advise being patient and using the older version that works until the new version comes out. You will have to do a fresh reinstall for sure. If you have questions I bet you could ask on the eeebuntu forums. 

Or you could switch back to Ubuntu, in which case we could help you here on these forums. :) It is certainly worth taking Ubuntu 9.10 for a test drive, maybe your wireless will work out of the box?

---

### Post by redcrystalmoon on 2010-02-08
Thanks for your reply... looks like I got some decisions to make ;o)

---

