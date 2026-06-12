---
title: "WUSB11 trouble"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by superduperlinuxperson on 2011-06-13
Hi!
i am having trouble getting my 2.4 GHz, 802.11b wireless adapter to work. it uses usb, and lsusb pulls it up. i also have tried ndiswrapper, but although it says its loaded, i cant find it anywhere! the version is 2.6. any help is appreciated!!
thanks:popcorn::p;);):D

---

### Post by chili555 on 2011-06-13
Please post:```
dmesg | grep ndis
ndiswrapper -l
```Thanks.

---

### Post by superduperlinuxperson on 2011-06-13
ndiswrapper -l:
autorun : invalid driver!
netusb : driver installed
dmesg | grep ndis:
[97915.947871] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[97916.246233] ndiswrapper (load_wrap_driver:108 : couldn't load driver netusb; check system log for messages from 'loadndisdriver'
[97916.246347] usbcore: registered new interface driver ndiswrapper
[146894.516104] ndiswrapper (load_wrap_driver:108 : couldn't load driver netusb; check system log for messages from 'loadndisdriver'
[147688.534390] ndiswrapper (load_wrap_driver:108 : couldn't load driver netusb; check system log for messages from 'loadndisdriver'

---

### Post by chili555 on 2011-06-13
It looks like you have loaded other than the XP .inf file in ndiswrapper. This is from *man ndiswrapper-1.9*:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install **Windows XP** drivers and kernel module to load the **Windows XP** drivers. Both are called ndiswrapper.I suggest you do:```
sudo ndiswrapper -e autorun
```Then check your work to see if you loaded the Vista or 7 or 98, etc. Windows .inf file.

---

### Post by superduperlinuxperson on 2011-06-13
autorun.inf is not the correct file becuse it controlls the image and name of your media. its only three lines long!
i will try it with netusb tough
btw it actually finds the linksys router on the usb id!

---

### Post by chili555 on 2011-06-13
> btw it actually finds the linksys router on the usb id!Then you're all set?

---

### Post by superduperlinuxperson on 2011-06-14
one would think so, but when i plug it in, nothing happens!!

---

### Post by chili555 on 2011-06-14
> It looks like you have loaded other than the XP .inf file in ndiswrapper. Have you addressed that issue?

---

### Post by superduperlinuxperson on 2011-06-17
turns out that the ndisgtk glitched, and it now also says that netusb is not the correct .inf file

---

### Post by chili555 on 2011-06-17
See post #4 above.

---

