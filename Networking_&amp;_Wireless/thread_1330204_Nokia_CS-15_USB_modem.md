---
title: "Nokia CS-15 USB modem"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by HandeH on 2009-11-18
There is a bandwidth problem when using Nokia CS-15 USB GSM/3G modem in Jaunty. When tested on [speedtest.net]("http://www.speedtest.net/") the bandwidth is only about 1,0 Mb/s but in Hardy the speed is about 1,9 Mb/s. Normal web surfing in Jaunty is **very sluggish**: pages are often crawling open at 0,16 Mb/s – 0,36 Mb/s.

This bug occurs also when dowloading a big file (for example from download.com or [download.fi]("http://www.download.fi")):
[LIST]
[*]The speed in Hardy 160–180 kB/s (occasionally also 270 kB/s)
[*]The speed in Jaunty only 40–45 kB/s (occasionally only 26–30 kB/s).
[/LIST]

On the other hand, **torrents seems** to be downloading at **correct** speed also in Jaunty, that is at 250–300 kB/s (as 300 kB/s = 2,4 Mb/s is the percieved de facto maximum speed of my Sonera so called 3,6 Mb/s mobile broadband subscriber connection). 

By the way, there is also a **regression in Karmic**: Nokia CS-15 USB modem do not work anymore and cannot be installed on 9.10 Karmic Koala. So, do not upgrade if you are need this modem.

---

### Post by Menestrello on 2009-11-18
I had a problem on karmic with Nokia CS-10, and it's now solved... maybe you can solve yours in the same way.

Check [http://ubuntuforums.org/showthread.php?t=1310892](http://ubuntuforums.org/showthread.php?t=1310892)

---

### Post by Whigu on 2010-01-20
> **HandeH said:**
> 
By the way, there is also a **regression in Karmic**: Nokia CS-15 USB modem do not work anymore and cannot be installed on 9.10 Karmic Koala. So, do not upgrade if you are need this modem.

I'm really sorry if somebody takes this as spamming but I wrote about how to get Nokia CS-15 to work in newest Ubuntu:
[http://www.petrilopia.net/wordpress/hardware/nokia-cs-15-and-linux/](http://www.petrilopia.net/wordpress/hardware/nokia-cs-15-and-linux/)

---

### Post by HandeH on 2010-03-06
There is a bug report about a performance issue: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/525049](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/525049)

The CS-15 does not work with Lucid Lynx 10.04 alpha3. You have to make a udev rule, but after that you can connect with NetworkManager. A bit of instructions can be found here: 
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/496256/comments/5](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/496256/comments/5)

---

### Post by Whigu on 2010-05-24
> **Whigu said:**
> I'm really sorry if somebody takes this as spamming but I wrote about how to get Nokia CS-15 to work in newest Ubuntu:
[http://www.petrilopia.net/wordpress/hardware/nokia-cs-15-and-linux/](http://www.petrilopia.net/wordpress/hardware/nokia-cs-15-and-linux/)

CS15 works even easier on Ubuntu 10.04 Lucid Lynx =) I updated that page little bit.
It's so easy to get work just with eject command that I use it with Live Ubuntu (CD and USB) often when I just need quick access to internet =)

---

### Post by HandeH on 2010-05-25
As Whigu wrote just a simple command after pluging in the CS-15 seems to be enough:
```
eject /dev/sr1
```

Before knowing that I first uninstalled wvdial and proceeded as earlier by making a file: 
```
gksu gedit /etc/udev/rules.d/25-usb_modem.rules
```
which consisted of: 
> # nokia cs-15
BUS=="usb", SUBSYSTEM=="block", SYSFS{idVendor}=="0421", SYSFS{idProduct}=="0610", ACTION=="add", RUN+="/usr/bin/eject -s %N", OPTIONS+="last_rule"

then gave a command:
```
sudo udevadm control --reload-rules
```
And after a while NetworkManager handled the rest...

---

### Post by Whigu on 2010-10-26
With Ubuntu 10.10 it's even easier to get Nokia CS-15 working... I wrote short "tutorial" kind of post about it:
[http://www.petrilopia.net/wordpress/software/ubuntu-1010-nokia-cs15/](http://www.petrilopia.net/wordpress/software/ubuntu-1010-nokia-cs15/)

It's done for Finnish operator but it should not be too hard to get work with others too =)

---

### Post by lenu on 2011-06-28
running 11.04 (mint), anyone else having problems with the cs-15 getting too hot (apparently) and disconnecting as a consequence?

*edit:* upgrading to 11.10 seems to improve the situation.

---

