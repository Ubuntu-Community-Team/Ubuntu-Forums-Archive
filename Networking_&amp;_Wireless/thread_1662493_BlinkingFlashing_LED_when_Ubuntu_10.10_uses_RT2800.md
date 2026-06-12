---
title: "Blinking/Flashing LED when Ubuntu 10.10 uses RT2800 instead of RT3090"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by cousinzoidfarb on 2011-01-08
Just posting this so others can find the solution more easily than I did.

My HP ProBook 4520s had a blinking/flashing wireless indicator LED and the connection was unstable. The solution was to blacklist the rt2800pci drivers. This leaves the rt2860sta drivers, which work fine for me (so far). The device is actually a RaLink RT3090 and apparently they release drivers on their web site, but I did not want to go through the trouble of building it and did not find it packaged for 10.10.

To try this fix, open up the blacklist file.
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
And add this line at the end...
```
blacklist rt2800pci
```

All credit goes to Linuxexperte, who posted here and perhaps elsewhere:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/113]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/113")

Good luck!

---

### Post by iyer.rajasekaran on 2011-01-25
Worked perfectly for me in HP ProBook 4520s made specially for windows7. I am using ubuntu 10.10. Thanks.):P

---

### Post by Ryazanov on 2011-04-19
Thanks a lot! It did fix as well problem with Ubuntu unable to shutdown properly. Probably was a wireless driver problem.
I'm using Natty beta 2 on HP ProBook 4520s.
Thanks again!

---

### Post by nikkobautista on 2011-05-01
:KS

This has been extremely helpful for me. I registered JUST to say thanks!

Btw, my laptop was a ProBook 4421s. What I did was I looked for what kind of driver my laptop was using:

nikko@nikko-HP-ProBook-4421s-ubuntu:~$ **lspci | grep -i wireless**
44:00.0 Network controller: Ralink corp. **RT2800** Wireless 802.11n 1T/1R PCIe

Once I found out that it was using RT2800, I just googled it and this was the first thread to come up.

Those who stumbled upon this thread, please try the following as well, it might help you with this frustrating issue!

Thanks again to **cousinzoidfarb!**

---

### Post by lfcfan on 2012-01-28
Hello everyone,
I am facing an issue with the above.
I blacklisted all rt2800 and rebooted my computer. I then installed rt3090-dkms, here is the result :
*****************************************************************************
(Reading database ... 208867 files and directories currently installed.)
Preparing to replace rt3090-dkms 1:2.4.0.4-0ubuntu0~ppa0 (using .../rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement rt3090-dkms ...
Setting up rt3090-dkms (1:2.4.0.4-0ubuntu0~ppa0) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.
Done
*****************************************************************************

But the it looks like the module is not installed :

*****************************************************************************
thierryk@thierry-HP-ProBook-4320s:/etc/modprobe.d$ sudo modprobe rt3090sta
[sudo] password for thierryk: 
FATAL: Module rt3090sta not found.
thierryk@thierry-HP-ProBook-4320s:/etc/modprobe.d$ sudo modprobe rt3090
FATAL: Module rt3090 not found.
thierryk@thierry-HP-ProBook-4320s:/etc/modprobe.d$ sudo modprobe rt3090-dkms
FATAL: Module rt3090_dkms not found.

thierryk@thierry-HP-ProBook-4320s:/etc/modprobe.d$ lspci -k|grep -i network --after-context 3
43:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
        Subsystem: Hewlett-Packard Company Device 1453
        Kernel modules: rt2800pci
44:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
*****************************************************************************

If I load the rt2800, it works (see the last line) :
*****************************************************************************
thierryk@thierry-HP-ProBook-4320s:/etc/modprobe.d$ sudo modprobe rt2800pci
thierryk@thierry-HP-ProBook-4320s:/etc/modprobe.d$ lspci -k|grep -i network --after-context 3
43:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
        Subsystem: Hewlett-Packard Company Device 1453
        Kernel driver in use: rt2800pci
        Kernel modules: rt2800pci

*****************************************************************************

Any idea to help me out please ?
Thanks in advance. Thierry

---

