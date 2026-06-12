---
title: "Linksys WUSB54GP Not Found, Can't Connect to Wireless - 10.04 Lucid Lynx"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by Vortex64 on 2010-06-05
**Linksys WUSB54GP Not Found, Can't Connect to Wireless -  10.04 Lucid Lynx** 			
 			 			 		   		 		 		Hi all,

I am having a problem setting up my wireless on Ubuntu 10.04 (Lucid  Lynx) on my desktop computer using a Linksys Wireless-G Portable USB  Adapter WUSB54GP.

The wireless has run fine on my Thinkpad X60s laptop running Lucid and  with my desktop and the same USB adapter in Karmic (9.10).  When I  installed Lucid as an upgrade on the desktop, I could not see the  adapter listed at all and could not connect wirelessly to the internet.

If someone could please let me know if I need to install drivers, edit a  file, or do something else to get this working I would greatly  appreciate it; I couldn't find anything useful to actually solve my  problem after searching for a while.

This should be all the important desktop system specs:[INDENT]  Linksys Wireless-G Portable USB Adapter WUSB54GP  -- not found; can't  connect to wireless internet
Lucid Lynx 10.04 (straight install from CD from Canonical)
Intel Pentium 4 630HT
ATI Radeon 4650HD
[/INDENT]Thank you in advance very much for any help!

---

### Post by Vortex64 on 2010-06-06
Just to clarify, I cannot see the device listed as a wireless device when checking in the terminal and I have no option to even connect to any wireless network on my desktop.  This issue did not happen with 9.10, and after putting in that cd to check, the wireless worked fine.  It seems to be only on 10.04 that the adapter is not recognized. :(

---

### Post by rchille on 2010-06-06
I seem to be have the same issue. An 'lsusb' comes back with the address and a "Linksys (?)":

```

rob@kitt:~$ lsusb
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 046d:c404 Logitech, Inc. TrackMan Wheel
**Bus 001 Device 007: ID 5041:2235 Linksys (?)** 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Is this what you are seeing?

---

### Post by chili555 on 2010-06-06
> ID 5041:2235 LinksysThis device is supposed to be driven by the module *p54usb.* Let's load it and see if an interface was created and if the kernel reports any problems:```
sudo modprobe p54usb
iwconfig
dmesg | grep p54
```Thanks.

---

### Post by Vortex64 on 2010-06-09
> **rchille said:**
> 
Is this what you are seeing?

That is exactly what I got when I ran that code after being advised here: [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/113666](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/113666)

@chili555:
  I ran that code and these were the results.

```
desktop:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

desktop:~# dmesg | grep p54
[    5.974034] usb 1-3: (p54usb) cannot load firmware isl3886usb (-2)!
[    5.977369] p54usb: probe of 1-3:1.0 failed with error -2
[    5.977416] usbcore: registered new interface driver p54usb
[  860.944607] usb 1-5: (p54usb) cannot load firmware isl3886usb (-2)!
[  860.953331] p54usb: probe of 1-5:1.0 failed with error -2

```
I'm not sure what to make of this error message. :)

It looks like the adapter is just not being found at all.  I was thinking about searching manually for the driver (I think I need rt2570) online or in synaptic and then installing it and hoping it would work out.

---

### Post by chili555 on 2010-06-09
> (I think I need rt2570) Incorrect.

This is the problem:> usb 1-3: (p54usb) cannot load firmware isl3886usb (-2)!Please open Synaptic and install *linux-firmware-nonfree*. Restart your computer and see if the wireless is now working.

---

### Post by Vortex64 on 2010-06-09
Thank you so much for the help chili555, that solved the problem!  I really appreciate it, thanks so much again! :D

---

### Post by Mistiq Dragon on 2010-12-05
> **chili555 said:**
> Incorrect.

This is the problem:Please open Synaptic and install *linux-firmware-nonfree*. Restart your computer and see if the wireless is now working.

I know this is months later, but I just wanted to say thank you.  This was so very helpful    :popcorn:

---

### Post by chili555 on 2010-12-05
Thanks! I love popcorn and I really love it when old posts help searchers for months to come. 

Have fun.

---

