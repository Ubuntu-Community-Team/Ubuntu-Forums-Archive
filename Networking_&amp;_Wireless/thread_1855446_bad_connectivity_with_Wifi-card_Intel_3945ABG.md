---
title: "bad connectivity with Wifi-card Intel 3945ABG"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by Karottenbaum on 2011-10-06
first of all: hallo!
excuse me for my English, i may use some odd expressions which makes you think for a while..

anyway, i installed xubuntu as a first time linux-user on an acer laptop and i really like it so far.
the only drawback is the wireless connection.

let me explain: the wifi is an "intel PRO/Wireless 3945ABG".
im using an hotspot a litle far away from my location, but under windows it worked quite good.
yeah, sometimes i lost connection, and the overall behavior was comprehensible because of the distant hotspot.
but i was able to establish connection from my room/desk without having to move my laptop.

now, before i installed xubuntu i tryed a couple of LIVE-CD distributions and i noticed the low WIFI-signal, it couldnt connect to the hotspot from my desk. 
i had to go in another room at the other end of my flat near to the window to establish connection.
same with xubuntu now. but when i made my walk to the other end, i could go back to my desk and work with a more good or less (more less) connection.
of course i have to go to the other side of the flat really often, because the signal gets lost quite quick.
what i think its strange that the connection itself gives me about 800 KB/s most of the time. so why the problem with establishing connection wit the router!?!?


** under windows i was able to tweak the driver with less power-saving/more signal-strength, and a couple of more options which helped me to stay at my desk with better signal.**


i was thinking of installing a driver from [http://www.intellinuxwireless.org](http://www.intellinuxwireless.org) but it seems to be an odyssey for a beginner like me, but i would if necessary - its fun too!


on [intellinuxwireless.org]("http://ubuntuforums.org/intellinuxwireless.org") they say *"Note: The iwlwifi driver has been merged into mainline kernel since 2.6.24. If you are using kernels after this release, please use the intree (drivers/net/wireless/iwlwifi) driver directly."*

on [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) is the whole install process explained.

[B]
should i update  like on [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) explained?
are there some config-files i could play around with and maybe get it to  work better, or maybe its just the "network Manager"App making these  troubles?[/B]


***my kernel:***
```
andi@acer:~$ uname -a
Linux acer 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 i686 i386 GNU/Linux
```***drivers used:***
```
andi@acer:~$ lspci -vv -s 05:00.0
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 44
    Region 0: Memory at d0100000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
```

---

### Post by Karottenbaum on 2011-10-06
i think im gonna try to change the "NetworkManager" to a few different other options but i think its not the source of the problem.


does anyone know where on the system im able to mess around with wifi settings or driver settings (conf files and so on..)?


Greets

---

### Post by wildmanne39 on 2011-10-06
Hi, if you start messing with settings and config files you will probably break wireless all together, please try this.
```
sudo ifconfig wlan0 down
sudo rmmod -f iwl3945
sudo modprobe iwl3945 11n_disable=1
sudo ifconfig wlan0 up

```
run the commands one at a time and if your wireless improves we will need to make it permanent.
Thank you

---

### Post by Karottenbaum on 2011-10-07
hi, i switched overnight to opensuse, there i did the commands... i think that was a misstake.
could bring wlan0 up again...

anyway, i reinstalled xubuntu - didnt liked opensuse at all... 

but i kepp that command in mind, i got an USB-stick now from a friend and it works again.

thanks alot for the help!

```
andi@acer # ifconfig wlan0 down
andi@acero # rmmod -f iwl3945
andi@acer # modprobe iwl3945 11n_disable=1
FATAL: Error inserting iwl3945 (/lib/modules/2.6.37.1-1.2-desktop/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
andi@acer # ifconfig wlan0 up
wlan0: unknown interface: No such device
```

---

### Post by wildmanne39 on 2011-10-07
Hi, your welcome!

---

### Post by Karottenbaum on 2011-10-08
well, the usb stick is a thing its not that reliable -  but for another reason.

the command batch you postet, is something of that still in the system? because i can connect now from my desk.

by the way i had the exact same error in xubuntu. but could it did something good, even after reboot (wlan0 came up again)?

because after that it feels much better... maybe its just a coincidence.

do you have an idea about the FATAL ERROR?

thanks

---

### Post by wildmanne39 on 2011-10-08
Hi, the fatal error just means it did not like the the command.

As for the rest what problem are you having with the usb adapter? please post:
```
lsusb
```
and we can take a look.
Thank you

---

### Post by Karottenbaum on 2011-10-08
hi, gave it back to my friend, he needed it.
so im back with my 3945ABG... its a little better now, but have you any tips for making it more stable?

greets!

---

### Post by wildmanne39 on 2011-10-08
Hi, I have been researching this issue and it is a bug that goes way back some say they fixed the problem by setting the speed in there router to b,g,n and not just n, or get rid of the n altogether, that is what I was trying to do with the commands that gave a fatal error so you will have to change the setting manually in your router.

Some people say they installed wicd and that fixed there problem, that application is in synaptic,if you are going to install wicd install it first then uninstall network manager, then restart your computer.
Thank you

---

### Post by chili555 on 2011-10-08
The Intel 3945ABG will not work with N _only_ router settings. The parameter given above is not therefor a valid parameter; you can't disable N because it can't do N at all. Please see *modinfo iwl3945*:> filename:       /lib/modules/2.6.38-11-generic/updates/cw-2.6.39/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945[COLOR="Red"]ABG/BG[/COLOR] Network Connection driver for Linux
srcversion:     E6FC24ED965A870B76D2D28
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwl-legacy,cfg80211,mac80211
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)Perhaps this will be helpful: [http://ubuntuforums.org/showthread.php?t=1837729&highlight=Intel](http://ubuntuforums.org/showthread.php?t=1837729&highlight=Intel)

---

### Post by wildmanne39 on 2011-10-08
Hi, that link may take care of your problem, the way I did the google search I never came across that link, but I approached it from the wrong angle, instead of getting the dmesg logs.

I noticed after the fatal error mesasage that it was not a valid paramter for your card and driver, that is when I ran modinfo, sometimes I don't check it first like I should but I hope that I will not do that again. I am sorry for that code, but it did not apply and it did no harm.

Thank you chili555 for the link it looks like what we need.

---

### Post by andylinux on 2011-10-09
Have you had a look at this bug?  I have been having this problem for months now.  You can see some of my comments on the bug.  If I switch to the windows drivers using ndiswrapper and use the windows drivers then I don't have the speed issue but sometimes I don't get a wireless connection when my machines comes out of suspend.  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265)

Based on this comment my problem seems to be associated with the 3945 wireless and my particular sub system.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265/comments/362](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265/comments/362)

What is the output of this command for you,
lspci -vnn | grep -A 1 Wireless  ?

---

### Post by Karottenbaum on 2011-10-09
no problem wildmanne39, i wish i knew as much as you! i still learned something. thanks.  i think the link really worked but ill give it a couple of days... thanks for the link too!  thx

---

### Post by wildmanne39 on 2011-10-09
Hi, I hope it did. We are all still learning.
Thank you

---

