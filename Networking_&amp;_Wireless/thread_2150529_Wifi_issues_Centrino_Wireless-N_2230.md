---
title: "Wifi issues: Centrino Wireless-N 2230"
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by bart.vanaudenhove on 2013-06-01
HP Envy dv7 7390eb, WIndows 8 UEFI pre-installed and fresh Ubuntu 12.04 LTS dual boot fresh install. No wireless, as far as ubuntu is concerned it's "hardware disabled" and putting the button (F12) does change the color of the led from inactive to active, but the "hardware disabled" status remains...

I found some threads here but am not knowledgeable enough to to something intelligent with them:
[http://askubuntu.com/questions/174472/how-to-get-intel-centrino-wireless-n-2230-to-work-on-11-10](http://askubuntu.com/questions/174472/how-to-get-intel-centrino-wireless-n-2230-to-work-on-11-10)
[http://ubuntuforums.org/showthread.php?t=2062633](http://ubuntuforums.org/showthread.php?t=2062633)
[http://ubuntuforums.org/showthread.php?t=2089512](http://ubuntuforums.org/showthread.php?t=2089512)
[http://wireless.kernel.org/en/users/Drivers/iwlwifi/?p=iwlwifi&n=downloads](http://wireless.kernel.org/en/users/Drivers/iwlwifi/?p=iwlwifi&n=downloads) (

Output of
```
ls -al /lib/firmware/iwlwifi-2030-*
```
is
```
-rw-r--r-- 1 root root 707392 Nov 16  2012 /lib/firmware/iwlwifi-2030-6.ucode
```

Output of 
```
sudo lshw -C network
```
gives
```
*-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: wlan0
       version: c4
       serial: 60:6c:66:05:bc:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-32-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:46 memory:73500000-73501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 07
       serial: a0:b3:cc:50:0c:69
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:73404000-73404fff memory:73400000-73403fff

```

---

### Post by cico.sail on 2013-06-01
Hi Bart
I have enable the wifi with this two steps:
1. from the attachment you have extract the driver for our chart put it in /lib/firmware;
2. then you have to upgrade the linux kernel to version 3.7.2 or mayor and restart.

Note: the F12 key is always disabled: it can have the color red or blue but this has no effect on wireless.
You can enable or disable it by software on net device control panel or command line 
```
rfkill [options]
```

[ATTACH]243378[/ATTACH]

---

### Post by wildmanne39 on 2013-06-01
You do not have the same device > Centrino Wireless-N 2230I suggest you start your own thread!
Thanks

---

### Post by Bucky Ball on 2013-06-01
***Post moved to own thread***

@ bart.vanaudenhove: I have moved your post to its own thread with a title that relates to your issue and edited accordingly. You can change the post anytime or the title within half hour or I can change the title after that if you want. This gives you a better chance of finding help rather than burying yourself on a thread that hasn't seen action for two months with a title that doesn't relate exactly to your problem.

Please post a new thread about your issues rather than jumping on someone else's (hijacking). This is unfair to the original OP, confusing and dilutes community effort.  

Good luck.

---

### Post by bart.vanaudenhove on 2013-06-01
> **Bucky Ball said:**
> ***Post moved to own thread***

@ bart.vanaudenhove: I have moved your post to its own thread with a title that relates to your issue and edited accordingly. You can change the post anytime or the title within half hour or I can change the title after that if you want. This gives you a better chance of finding help rather than burying yourself on a thread that hasn't seen action for two months with a title that doesn't relate exactly to your problem.

Please post a new thread about your issues rather than jumping on someone else's (hijacking). This is unfair to the original OP, confusing and dilutes community effort.  

Good luck.

OK, sorry, still learning, thanks for the explanation and help :KS

---

### Post by bart.vanaudenhove on 2013-06-01
> **cico.sail said:**
> 
I have enable the wifi with this two steps:
1. from the attachment you have extract the driver for our chart put it in /lib/firmware;
2. then you have to upgrade the linux kernel to version 3.7.2 or mayor and restart.
[ATTACH]243378[/ATTACH]

OK, thanks. I'm a bit confused about someone posting "You don't have the same device", but anyway I can find the appropiate driver and .tar file on the [iwlwifi site]("http://wireless.kernel.org/en/users/Drivers/iwlwifi/?p=iwlwifi&n=downloads") I guess and put that in /lib/firmware.
But concerning kernel upgrade:
1) I would like to stick with Ubuntu 12.04.2 LTS, I imagine that a kernel upgrade actually brings me to another Ubuntu version?
2) how do I do a kernel upgrade ?!?

Thanks for the interest and help...

---

### Post by Bucky Ball on 2013-06-01
No, kernel upgrade won't take you to the next release. Issue these two commands, one at a time;

```
sudo apt-get update
sudo apt-get upgrade
```

That will upgrade all packages and software but will not upgrade you to the next release. That is a different command. If there is a newer kernel, the upgrade command above will add it. You an also upgrade to very new kernels manually by adding the PPA (you can run the Raring kernels in 12.04 for instance) but that won't happen automatically. I run the Raring kernel occasionally just like this because Raring has the drivers for a piece of hardware of have whereas 12.04 kernel does not. 

Reboot after the update/upgrade and see if there's wifi then. If not, post the output of:

```
iwconfig
```

Sometimes there can be problems with wireless N and needs to be switched off at the local machine (maybe your router isn't N and can't deal with that) or there could be some other reason. I don't know how to switch off N so hopefully someone more expert can pipe up. ;)

---

### Post by ahallubuntu on 2013-06-01
~

---

### Post by bart.vanaudenhove on 2013-06-02
> **Bucky Ball said:**
> No, kernel upgrade won't take you to the next release. Issue these two commands, one at a time;

```
sudo apt-get update
sudo apt-get upgrade
```

That will upgrade all packages and software but will not upgrade you to the next release. That is a different command.

I don't quite get the difference then between upgrading all packages and software, and changing release. I want to install "once and for all" my system, get it running, and then never have to look at it again (or as little as possible) until april 2017. Bu if I upgrade all packages and software, I'll be getting more or less "unstable" packages, right? I mean, compared to the LTS packages...
Don't mean to be a wiseguy, just really trying to understand... I want maximum stability...

---

### Post by bart.vanaudenhove on 2013-06-02
Hi ahallubuntu, interesting, thanks.
```
rfkill list all
``` gives
```
0: phy0: Wireless LAN    Soft blocked: yes
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```
so indeed no hard block.

And
```
sudo rfkill unblock all
```
did actually enable my wireless, it got status "enabled" in the net applet, and ```
rfkill list all
``` gives
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```So I guess that's SOLVED :D Thanks!! And without installing or changing anything in my setup. Brilliant!

I also tested with Wifi-radar and everything works.

(And thanks also to other people who responded on this thread for their time and effort and good will.)

---

### Post by Bucky Ball on 2013-06-02
> **bart.vanaudenhove said:**
> I don't quite get the difference then between upgrading all packages and software, and changing release. I want to install "once and for all" my system, get it running, and then never have to look at it again (or as little as possible) until april 2017. Bu if I upgrade all packages and software, I'll be getting more or less "unstable" packages, right? 

Nope. Not if you are running the LTS version. You will be getting the stable updates for the LTS release and not unstable ones. Any programs you have installed will be upgraded if there is a newer version and it is in the 12.04 repos. The kernel difference is in the numbering, among other things. Raring runs 3.9.** while 12.04 LTS runs 3.2.**. You will not get updates for the 3.9 kernel if you were running the 3.2 series. That would make 12.04 unstable. Someone else may wish to elaborate ...

If you have 12.04 LTS installed, don't bother with much until April 2017. If things are running fine, there is little to no chance an update or sudo apt-get upgrade will ever break it. Good luck and glad you got the wireless up. Post a new thread for further issues, enjoy the OS, the forums and the learning curve. ;)

---

