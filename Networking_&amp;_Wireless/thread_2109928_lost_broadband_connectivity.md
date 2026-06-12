---
title: "lost broadband connectivity"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by jimeast on 2013-01-28
I have a Dell Latitude d620 with an internal broadband card.  I run both Vista and Ubuntu 12.10 client in a dual boot configuration.  I used to get broadband on both OS's but now I get the message "Network Disconnected - you are now offline" whenever I boot into Ubuntu.  I'm very new to Linux and don't know how to configure and test these things.

---

### Post by TOMBSTONEV2 on 2013-01-28
Please identify your wireless network card with
```
lspci
```

---

### Post by jimeast on 2013-01-28
I have:
Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigibet Ethernet PCI Express (rev 02)
and
Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I think Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) is the wireless card.

---

### Post by TOMBSTONEV2 on 2013-01-28
Yes you are correct; the Broadcom BCM4311 is your wireless adapter.

Please try this:
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```If that does not work I would like you to visit this webpage and install the b43-fwcutter firmware, than install the b43 drivers.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I usually find people have more success installing the b43 firmware and b43 drivers. To do so download the firmware from:

[https://launchpad.net/debian/sid/+source/b43-fwcutter/1:015-14/+files/b43-fwcutter_015.orig.tar.bz2](https://launchpad.net/debian/sid/+source/b43-fwcutter/1:015-14/+files/b43-fwcutter_015.orig.tar.bz2)

and download the b43 driver:

[http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2)

Copy both to your home folder then open a terminal and type:

cd /home/your_user_name/b43-fwcutter-015

After this type: 

sudo make
sudo make install

This will install the b43 firmware. Open a new terminal and type:
```

tar xfvj broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
```Restart your computer then open a terminal and type:

```
sudo modprobe b43
```

---

### Post by jimeast on 2013-01-28
Thanks for your help.  I'll go over this in the morning when I can think a little more clearly.

---

### Post by jimeast on 2013-01-29
It worked!!!
thank you so much!!

---

### Post by TOMBSTONEV2 on 2013-01-29
No problem my friend, please mark this thread as solved. =)

---

### Post by jimeast on 2013-02-02
Now I'm lost it again.  After a happy day or so using my broadband I plugged back into my Ethernet after a day I unplugged the Ethernet cable and tried to use broadband and it's not there?  Any ideas how I can best track down this problem?  How would I see if the changes I made were still there?

---

### Post by TOMBSTONEV2 on 2013-02-02
Aye, please enter:
```
sudo lshw -C network
```into a terminal and please post the output here.

---

### Post by jimeast on 2013-02-22
This is what I get:
jim@jim-Latitude-D620:~$ sudo lshw -C network 
[sudo] password for jim: 
  *-network UNCLAIMED     
       description: Network controller 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:efdfc000-efdfffff 
  *-network DISABLED 
       description: Ethernet interface 
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:15:c5:48:e6:45 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:18 memory:efcf0000-efcfffff 
jim@jim-Latitude-D620:~$

---

### Post by TOMBSTONEV2 on 2013-02-23
See this is particularly odd, essentially its telling us that you have no driver installed for it. Try:

```
sudo modprobe b43
```

See if that works again. I have no idea as to how or why the drivers became uninstalled. I do know that it is uncommon for this to occur after the b43 drivers have been installed.

---

### Post by varunendra on 2013-02-23
*Thread moved to **Networking & Wireless**.*

---

