---
title: "wifi on Lenovo IdeaPad N581"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by dreusser on 2013-02-22
The wifi on Lenovo IdeaPad N581 worked after installation from an older Ubuntu 12.04LTS CD. After installing the available updates, access stopped working.

After searching and experimenting, the following worked:

> lspci -nnk | grep -iA5 net

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0587]

The bcmwl module did not work, however, I got the broadcom-sta packages to work:


> sudo apt-get install broadcom-sta-common
> sudo apt-get remove bcmwl-kernel-source


> sudo m-a a-i broadcom-sta

note that the driver sources currently need a small fix, documented here:

[bugs.debian.org/cgi-bin/bugreport.cgi?bug=656600]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=656600")


Afterwards, the wireless card worked for me.

---

### Post by alabamaIII on 2013-02-26
I tried the commands in the post above. The 3rd command reported Build Failed.

Then from an askubuntu thread, I tried the commands below.

Please check:

lspci -nn
Is it's pci.id 14e4:4727?
If so, this may be helpful:

sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source 
sudo modprobe wl

*My WiFi is now working.*

BEFORE all of the above commands I tried from the same askubuntu thread.

Go to system settings--> software sources --> Additional Drivers.
Then select 'Do not use this device'

This allowed my WiFi modem to connect, but at a speed of about 0.15Mb/s.

Then I ran the command

sudo apt-get build-dep linux

My Wifi began working as I would expect it to. But 5/6 hours later the WiFi stopped working, for no obvious reason.

---

