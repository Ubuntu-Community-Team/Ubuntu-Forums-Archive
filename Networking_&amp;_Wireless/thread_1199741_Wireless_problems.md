---
title: "Wireless problems"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by mutonchops on 2009-06-29
Hiya, I am a complete beginner with Ubuntu and I installed the most recent release on my Acer Aspire 7110 and there is no wireless network showing on my network manager. I have had a look on the help pages and it may have been a driver problem, so I have disabled the driver that was associated with my broadcom wireless card and used gui interface for ndiswrapper to install the windows driver for the card. 

It shows as recognising the hardware, however there still doesnt seem to be any wireless networks or any option to enable wireless in the top right. 

Can anyone offer any advice as to why this isnt working? If you need any extra information I can prodive that for you.

Thanks in advance.

---

### Post by mutonchops on 2009-06-29
Extra info - this is the lspci info for my wireless card:

0a:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Thanks

---

### Post by Ayuthia on 2009-06-29
Usually b43-fwcutter will get your wireless card working without NDISwrapper.  However since you have NDISwrapper installed, please try the following and see if any wireless sites appear (this is from the Terminal):
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```

---

### Post by mutonchops on 2009-06-29
hi,

I have tried all three of those commands with the following results:

sudo modprobe -r b43 ssb ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
russell@russell-laptop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
russell@russell-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     No scan results

Thanks,

R

---

### Post by Ayuthia on 2009-06-29
Can you post the results of:
```
ndiswrapper -l
dmesg|grep ndis
```
The messages that appear are warnings.  In Jaunty, the files in /etc/modprobe.d now have a .conf extension to them.  At some point you are going to have to copy the information in /etc/modprobe.d/blacklist and place them into /etc/modprobe.d/blacklist.conf.  At some point, I am guessing that ndiswrapper will be updated to have ndiswrapper change to ndiswrapper.conf.

The commands above will help us see if NDISwrapper recognizes the Windows driver and the second command checks to see if NDISwrapper is happy in the system.

---

### Post by mutonchops on 2009-06-29
Thanks Ayuthia, here is the response to those commands:

russell@russell-laptop:~$ ndiswrapper -l

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4318) present (alternate driver: ssb)
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5a : driver installed
    device (14E4:4318) present (alternate driver: ssb)

russell@russell-laptop:~$ dmesg|grep ndis

[10227.697441] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[10227.723110] usbcore: registered new interface driver ndiswrapper
[10269.153550] usbcore: deregistering interface driver ndiswrapper
[10269.169606] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[10269.180215] usbcore: registered new interface driver ndiswrapper
[18553.202183] usbcore: deregistering interface driver ndiswrapper
[18617.598043] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[18617.752410] ndiswrapper: driver bcmwl5a (Broadcom,12/22/2004, 3.100.46.0) loaded
[18617.752691] ndiswrapper 0000:0a:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[18617.762947] ndiswrapper: using IRQ 20
[18617.971354] usbcore: registered new interface driver ndiswrapper

Thanks.

---

### Post by Ayuthia on 2009-06-29
Everything looks right.  You might try installing b43-fwcutter to see if you can get the b43 module running instead.  Worst case, the b43 module might be able to provide more information on why your wireless card is not running.

---

### Post by mutonchops on 2009-06-29
I have installed the B43-fwcutter and now there is a wireless enabled option in the network manager, however, there is still no network showing under the connection. Do you have any idea as to why this is?

Thanks

---

### Post by mutonchops on 2009-07-02
I have got this to work now, I just needed to run an update and it worked after that. Thanks for your help.

---

