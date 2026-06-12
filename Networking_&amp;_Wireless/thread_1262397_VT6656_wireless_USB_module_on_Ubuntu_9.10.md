---
title: "VT6656 wireless USB module on Ubuntu 9.10"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by lunatichorse on 2009-09-09
Hi, I'm struggling to get a VIA VT6656 USB wireless module on a Zotac GeForce 9300 motherboard working with Ubuntu 9.10.

I downloaded the driver's sources from VIA support site (VT6656_Linux_src_v1.19_12_x86.zip), extracted it to a temp dir, and followed instructions inside the zip file:
sudo su
make clean
make install
insmod driver/vntwusb.ko
ifconfig eth1 up

Everything compiles without any errors, the driver seems to load fine, I can see the eth1 interface with ifconfig, and the network NetworkManager applet shows my network in range and everything, but it just doesn't succeed connecting and keeps asking for WPA password.

I also have Windows 7 on a different partition and everything works fine there, so that rules out any hardware defects or problems with my wireless network.

I was wondering if someone could give me a hand troubleshooting this?

Thanks

---

### Post by lunatichorse on 2009-09-09
Just realized that the driver doesn't seem to be loading properly.

lshw -C network
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:12:7b:47:a9:5d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11-a/b/g

Should I get a driver=vntwusb in the configuration line?

Forgot to mention that I added this to /etc/modules:
alias eth1 vntwusb

Is that the right place? Anything missing?

---

### Post by lunatichorse on 2009-09-10
Okay... I re-configured my wireless network to allow open (non-authenticated) connections and bingo! it connected. So that means the driver is actually properly installed/loaded and works.

Now the problem is WPA/WPA2 authentication. WEP didn't work either. There is a vague note about WPA authentication in a readme file that came with the sources mentioning that "Support supplicant(STA) wpa/wpa2 with wpa_supplicant-0.5.8". My package manager says I've got wpasupplicant 0.6.6.2 installed. Not sure if I need to compile the one distributed with the driver sources myself?

There's also another note saying "The 'wpa_supplicant-0.5.8' contains the extra file: 'driver_viawget.c' which is interface driver dedicated for 'vntwusb' linux driver." There are not makefiles or instructions to get that installed...

Anyone with experience on that?

These things really didn't need to be so complicated...

---

### Post by chupp on 2009-12-07
I am having similar experience with Debian 5.03 and have spent hours trying to figure out what I did wrong.  Did you compile wpa_supplicant-0.5.8 to see if it worked?  I'll do that tonight when I got home and post result if success.
Yes, these things needn't be so complicated.  At least, I learnt a lot more about Linux.

Later.

---

