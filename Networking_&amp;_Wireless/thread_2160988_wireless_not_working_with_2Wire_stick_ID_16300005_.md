---
title: "wireless not working with 2Wire stick ID 1630:0005 Intersil ISL3886usb ZD1211rw"
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by PCunicorn on 2013-07-09
I can not get Ubuntu (10.10) to work with the [COLOR=#444444][FONT=arial]ZyDAS ZD1211B chip. I have installed the driver from here [/FONT][/COLOR][http://zd1211.ath.cx/download/](http://zd1211.ath.cx/download/) and just can not get it to work. Ubuntu just says no network devices detected.
**UBUNTU 10.10 CAN NOT BE HELPED. THIS WAS SOLVED WITH XUBUNTU 12.04.**

---

### Post by PCunicorn on 2013-07-09
Bump

---

### Post by PCunicorn on 2013-07-09
bump

---

### Post by praseodym on 2013-07-09
You know that 10.10, 11.04 and 11.10 are outdated? I strongly recommend installing 12.04. Please show the outputs of
```

lsusb
lsmod
iwconfig
```

---

### Post by PCunicorn on 2013-07-09
I would of if 12.04 or 13.04 fit on a CD.

Lsmod (let me know if you need a better pic)
[IMG]http://i.imgur.com/bWyHBFHl.jpg?1[/IMG]

Lsusb
[IMG]http://i.imgur.com/7d6S4dtl.jpg[/IMG]

Iwconfig
[IMG]http://i.imgur.com/WEL63Xml.jpg[/IMG]

---

### Post by praseodym on 2013-07-09
Obviously, the stick is not recognized, it should read:

**ID 0ace:1215 ZyDAS ZD1211B 802.11g**

12.04 Netboot-CD-images here:

[http://cdimage.ubuntu.com/netboot/12.04/](http://cdimage.ubuntu.com/netboot/12.04/)

---

### Post by PCunicorn on 2013-07-09
What is ubuntu netboot? And will 12.04 support the card? Also if netboot is what I think it is, I can't use it as I have no ethernet.

---

### Post by praseodym on 2013-07-09
Yes it does.

---

### Post by PCunicorn on 2013-07-09
Damn, I don't have a DVD rom, to old for USB booting, and no ethernet card. I do have 700mb CDs though. Is there anyway to update 10.10 to 12.04 with a CD? So it will only have to install the updates, not an entire os which is to big for a CD. Also, does 11.10 support the card?
Edit: the alternate 32 bit 12.04 disk will work, but I used my last CD on fedora so I will have to buy some more.

---

### Post by praseodym on 2013-07-09
For an old computer try Xubuntu 12.04 LTS

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

or Lubuntu (no LTS)

[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/)

---

### Post by PCunicorn on 2013-07-09
I would prefer Ubuntu with Gnome 3. I have A fine GPU, but my CPU is around a first gen P4.

---

### Post by wildmanne39 on 2013-07-09
Please only bump once every 24 hours.

Also only one topic per thread so if you install a later version of ubuntu please start a new thread for that topic in the appropriate section of the forum like install and upgrades or general help if you need help with installation.
Thanks

---

### Post by praseodym on 2013-07-09
[http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/)

Maybe that? But still in development for 13.10

---

### Post by PCunicorn on 2013-07-10
Okay I am going to start a new thread, I got 12.04 lts 32 bit (non alternate) on a CD and it hangs on the first screen.

---

### Post by PCunicorn on 2013-07-10
i just installed xubuntu 12.04 and still no networking. **_&#8203;FOR FUTURE READERS: FOLLOW EVERYTHING BELOW_**

---

### Post by praseodym on 2013-07-10
Check:
```

sudo modprobe -rfv ndiswrapper
sudo modprobe -rfv zd1211rw
sudo modprobe -v zd1211rw
lsmod
rfkill list
```

---

### Post by PCunicorn on 2013-07-10
[IMG]http://i.imgur.com/mFiqv36l.jpg[/IMG]
Missing some of the bottom but nothing looked important.

---

### Post by praseodym on 2013-07-10
I can see another wrong driver loaded:
```

sudo modprobe -rfv p54usb
sudo modprobe -rfv zd1211rw
sudo modprobe -v zd1211rw
echo "blacklist p54usb" | sudo tee -a /etc/modprobe.d/blacklist.conf

```

---

### Post by PCunicorn on 2013-07-10
[IMG]http://i.imgur.com/XLYP311l.jpg[/IMG]
Should I restart the computer now?

---

### Post by praseodym on 2013-07-10
Re-plugging the stick should be enough. Check then

```
iwconfig
rfkill list
cat /etc/resolv.conf
route -n
```

---

### Post by PCunicorn on 2013-07-10
Says Rkill isn't installed, and iwconfig show no wireless devices.

---

### Post by praseodym on 2013-07-10
Is the stick recognized with
```

lsusb
```

---

### Post by PCunicorn on 2013-07-10
Yes, it is recognized with lsusb which is an improvement over 10.10 where it wasn't recognized with lsusb.

---

### Post by praseodym on 2013-07-10
With the same ID as I showed above?

---

### Post by PCunicorn on 2013-07-10
You tell me: (the 2wire is the network adapter.)
[IMG]http://i.imgur.com/RJcIXwsl.jpg[/IMG]

---

### Post by praseodym on 2013-07-10
Well,

we blacklisted the wrong one. Open the file
```

gksudo gedit /etc/modprobe.d/blacklist.conf
```
Replace the line
```
blacklist p54usb
```
with
```
blacklist zd1211rw
```
Save and close the editor. After that save this file in "Downloads":
[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Install it via
```

sudo dpkg -i ~/Downloads/*.deb
```Reboot.

---

### Post by PCunicorn on 2013-07-10
It worked! Holy crap man, thanks a ton. I owe you a beer :D

---

### Post by praseodym on 2013-07-10
:popcorn: 

Please change the thread title to something like "wireless not working with 2Wire stick ID 1630:0005 Intersil ISL3886usb" and edit the 1st posting to refer to the title change

---

