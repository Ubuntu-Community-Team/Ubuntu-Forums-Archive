---
title: "Atheros AR8131 - Wireless is Disabled by Hardware Switch"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by _user on 2011-07-20
Product Information: Medion P6627
Version: Ubuntu 11.04
Kernel: 2.6.38-10-generic x86_64

I'm unable to disable the 'wireless disabled by hardware switch' message.  I've tried rfkill unblock all - no effect.  It remains hard blocked after running the unblock command, rebooting, alternating the switch in windows, alternating the bios setting.  Wireless internet does not work because of this.

lspci: [http://pastebin.com/4iGdgSRj](http://pastebin.com/4iGdgSRj)
lsusb: [http://pastebin.com/PcRgJN20](http://pastebin.com/PcRgJN20)
ifconfig: [http://pastebin.com/fHJ5YZQk](http://pastebin.com/fHJ5YZQk)
iwconfig: [http://pastebin.com/2kYXe9hh](http://pastebin.com/2kYXe9hh)
lsmod: [http://pastebin.com/EbXeFDHt](http://pastebin.com/EbXeFDHt)
dmesg: [http://pastebin.com/ZxWFz0zg](http://pastebin.com/ZxWFz0zg)
sudo lshw -C network: [http://pastebin.com/2Az8RepA](http://pastebin.com/2Az8RepA)

==========

rfkill list:

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

==========

iwlist scan: 

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

==========

Any suggestions more than welcome!

---

### Post by thefasterblueone on 2011-07-20
rfkill list reports a hard block.

Using the Quick launch key combination Fn+F2 you can enable or disable the
wireless LAN function.

---

### Post by _user on 2011-07-20
Fn+F2 solved the problem.  Easy when you know how - thanks!

---

