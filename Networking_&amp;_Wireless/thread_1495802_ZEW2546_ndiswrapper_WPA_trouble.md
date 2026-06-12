---
title: "ZEW2546 ndiswrapper WPA trouble"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by Joe Awsome on 2010-05-28
Hey guys, posting this thread so that me and Chili555 could trouble shoot my driver and wifi problems, and help anyone with a similar problem. So on Monday my dad and brother decided to upgrade the wifi and secure it with a WPA hex key (IDK if it's WPA or WPA2). They had done this before, but luckily the router went bad and we switched back to our old unsecured G router. The problem is that I have never been able to connect to any encrypted wifi with my usb dongle using the suplied drivers and ndiswrapper. So when this happened a few days ago, I tried to use ndiswrapper troubleshooting guide pinned to this section of the forums, while doing that I discovered a native linux driver for my card (ZEW2546 using RTL8192SU chipset) and was wondering if this driver would work for my card and solve my WPA troubles. I have also had no luck finding an older windows driver for my card either and have read that the current windows driver is pretty sloppy on windows itself. So any ides?

Here is the code that told me about the alternate driver:

joe@joe-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8192su : driver installed
	device (0BDA:8172) present (alternate driver: r8192s_usb)

---

### Post by chili555 on 2010-05-28
> (alternate driver: r8192s_usb)First. let's see if it's loading and conflicting. Please post:```
lsmod | grep -e ndis -e 819
```Thanks.

---

### Post by Joe Awsome on 2010-05-29
here is what it spat out:

ndiswrapper           184677  0 

When i ran the ndiswrapper trouble shoot it said that it was loading ndiswrapper and not the native linux module. Do u have any info on this alternate linux module? Cuz I would like to try to run native if at all possible. I also read earlier that realtech doesn't have a native linux driver for the 10.04 kenrel, is this true?

---

### Post by chili555 on 2010-05-29
I don't know what version you are running, but in 10.04, r8192s_usb is present. You can check with:```
modinfo r8192s_usb
```It will either say there is no such module or it will say:> filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
version:        V 1.1
license:        GPL
etc, etc.Unless you know the module is present, we are stuck.

---

### Post by Joe Awsome on 2010-05-30
here's what I got:

modinfo r8192s_usb
joe@joe-desktop:~$ modinfo r8192s_usb
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
version:        V 1.1
license:        GPL
license:        GPL
description:    HostAP crypto
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: TKIP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: CCMP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: WEP
author:         Jouni Malinen
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
srcversion:     15129E557087B6D43A679C4
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0290d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3301d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0043d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8192d*dc*dsc*dp*ic*isc*ip*
depends:        
staging:        Y
vermagic:       2.6.32-22-generic SMP mod_unload modversions 586 
parm:           debug:debug output mask (int)
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware security support.  (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)

I am running Lubuntu 10.04 Lucid Lynx

---

### Post by chili555 on 2010-05-31
What is the result if you temporarily remove ndiswrapper and insert r8192s_usb?```
sudo rmmod -f ndiswrapper
sudo modprobe r8192s_usb
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by Joe Awsome on 2010-05-31
when I put in:
sudo modprobe r8192s_usb

I get:
WARNING: All config files need .conf:/ect/modprobe.d/ndiswrapper, it will be ignored in a future release.

---

### Post by chili555 on 2010-06-01
First, let's fix the warning. Please do:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf 
```Proofread carefully before you press the Enter key.

Now repeat the commands:```
sudo rmmod -f ndiswrapper
sudo modprobe r8192s_usb
iwconfig
sudo iwlist wlan0 scan
```Is there any output from the other commands?

---

### Post by Joe Awsome on 2010-06-01
here is what it spat out, I had to run the command twice because I forgot to keep LXterminal open when copy/pasting(hence the errors):


```
joe@joe-desktop:~$ sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
[sudo] password for joe: 
mv: cannot stat `/etc/modprobe.d/ndiswrapper': No such file or directory
joe@joe-desktop:~$ sudo rmmod -f ndiswrapperERROR: Removing 'ndiswrapper': No such file or directory
joe@joe-desktop:~$ sudo modprobe r8192s_usb
joe@joe-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

joe@joe-desktop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

joe@joe-desktop:~$
```

---

### Post by Joe Awsome on 2010-06-08
Is there any hope for my wifi setup Chili?

---

### Post by chili555 on 2010-06-08
Let's have a look at:```
dmesg | grep -e 819 -e ndis
```Thanks.

---

### Post by Joe Awsome on 2010-06-12
here is what I got:

```
[107819.037312] usb 1-2.3: reset full speed USB device using ehci_hcd and address 4
[107819.208302] usb 1-2.3: reset full speed USB device using ehci_hcd and address 4
[107819.380260] usb 1-2.3: reset full speed USB device using ehci_hcd and address 4
[107819.549396] usb 1-2.3: reset full speed USB device using ehci_hcd and address 4
[107819.721459] usb 1-2.3: reset full speed USB device using ehci_hcd and address 4
[107819.813690] usb 1-2.3: device descriptor read/all, error -32
[107819.885379] usb 1-2.3: reset full speed USB device using ehci_hcd and address 4
[107819.977666] usb 1-2.3: device descriptor read/all, error -32

```
Would using wpa supplicant and wpa_gui help me with my problems? because all I'm having trouble with is connecting to a wpa encrypted network, wifi works fine with no encryption. That's why I thought the ndiswpapper driver was at fault for it. Am I missing something that should be painfully obvious?

---

### Post by Joe Awsome on 2010-06-20
I AM AN IDIOT!!! My brother gave me the wrong password for the network! I checked with my dad and now I can connect! I am extremely sorry for all the trouble I put you through chilli :cry:
I just hope that this is the last time I ever do this to anyone else, I'm really sorry for this guys, and I feel horible for it, but the upside is that the advise given by chilli will help somebody else solve thier problem. I'm really sorry bout this.

---

### Post by divad531 on 2010-08-03
I have also had problems with My zonet usb wifi ZEW2546. I am using 10.04 and  I have gotten it to work a couple of times, but each time i did i did something different.  It never seems to work after I reboot the computer.  I have gone through several of the ubuntu wifi set ups.  I have tried both network manager and wicd with the same results.  the first time it worked was after setting up ndiswrapper, the second by downloading some of the files suggested by "nukedathlonman" from post #35 of [https://bugs.launchpad.net/ubuntu/+bug/572777](https://bugs.launchpad.net/ubuntu/+bug/572777) which others found success with, and the third time that it worked was after messing around with a few of the commands suggested here.  Since I am new to a lot of this I might be forgetting something, or having a misunderstanding somewhere.  here are the outputs to many of the codes suggested here:

```


david@david-desktop:~$ lsmod | grep -e ndis -e 819
r8192s_usb            346007  0 
ndiswrapper           184677  0 


@david-desktop:~$ modinfo r8192_usb
ERROR: modinfo: could not find module r8192_usb


david@david-desktop:~$ dmesg | grep -e 819 -e ndis
[    0.028196] ACPI: Core revision 20090903
[   13.226321] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   13.237243] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   13.284396] Linux kernel driver for RTL8192 based WLAN cards
[   13.674074] usbcore: registered new interface driver rtl819xU
[   13.674651] usbcore: registered new interface driver ndiswrapper
[   16.352359] rtl819xU: --->FirmwareDownload92S()
[   16.352376] usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   16.378301] rtl819xU:request firmware fail!
[   16.379880] rtl819xU:Firmware Download Fail!!a
[   16.388363] rtl819xU: --->FirmwareDownload92S()
[   16.388381] usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   16.399406] rtl819xU:request firmware fail!
[   16.399960] rtl819xU:Firmware Download Fail!!a
[   16.399968] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   21.065875] rtl819xU: --->FirmwareDownload92S()
[   21.065888] usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   21.069864] rtl819xU:request firmware fail!
[   21.070428] rtl819xU:Firmware Download Fail!!a
[   21.080379] rtl819xU: --->FirmwareDownload92S()
[   21.080396] usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   21.083821] rtl819xU:request firmware fail!
[   21.084757] rtl819xU:Firmware Download Fail!!a
[   21.084768] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   25.284281] rtl819xU: --->FirmwareDownload92S()
[   25.284299] usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   25.305975] rtl819xU:request firmware fail!
[   25.306556] rtl819xU:Firmware Download Fail!!a
[   25.315605] rtl819xU: --->FirmwareDownload92S()
[   25.315623] usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   25.361943] rtl819xU:request firmware fail!
[   25.362521] rtl819xU:Firmware Download Fail!!a
[   25.362531] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   29.160951] rtl819xU: --->FirmwareDownload92S()
[   29.160970] usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   29.181961] rtl819xU:request firmware fail!
[   29.181964] 
[   29.182532] rtl819xU:Firmware Download Fail!!a
[   29.194054] rtl819xU: --->FirmwareDownload92S()
[   29.194071] usb 1-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   29.207768] rtl819xU:request firmware fail!
[   29.208678] rtl819xU:Firmware Download Fail!!a
[   29.208689] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!


david@david-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down //the one i am trying to get to work




```

Any help would be appreciated

---

### Post by Unkuiri on 2010-08-03
Have you tried to remove the modules selectively, it can be a module conflict, in mine that happens, when I start my computer I always have to do: 
> sudo rmmod rt2800usb

In your case you can try first for example removing the r8192s_usb module and unplugging and replugging the device.
Using:
> sudo rmmod r8192s_usb
if it doesn't work, to load the module again, do:
> sudo modprobe r8192s_usb
do the same for ndiswrapper.

Hope this helps in some way...:)

---

### Post by divad531 on 2010-08-03
Wow, thanks Unkuiri, that seems to work great.  I appreciate the help.  Any possibilities of debugging the conflict that forms, or is the manual way of removing one pretty much the basic/only solution?  Thanks again.

---

### Post by Unkuiri on 2010-08-03
There maybe are other more definitive solutions that I'm not aware of, I'm not an expert, but you can make a starter in your desktop or panel and make it run the command you used to make the device work but instead of "sudo" use "gksudo" it's like a "graphical sudo" :P...
There is also a way to blacklist the module but I don't remember how to do it and maybe it can be dangerous because you could need this module for other devices...
Maybe other more experienced members can help you with that somewhat definitive solution...:)

---

### Post by chili555 on 2010-08-04
> **divad531 said:**
> Wow, thanks Unkuiri, that seems to work great.  I appreciate the help.  Any possibilities of debugging the conflict that forms, or is the manual way of removing one pretty much the basic/only solution?  Thanks again.What specific step did you take to get your wireless going? I am sure we can work out a proper permanent fix.

---

