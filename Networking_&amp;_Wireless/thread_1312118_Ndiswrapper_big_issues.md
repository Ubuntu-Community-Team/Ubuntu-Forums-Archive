---
title: "Ndiswrapper big issues"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by Axel-P on 2009-11-02
So!

I want to install my windows drivers with ndiswrapper which I have done plenty of times but now is not working.

If I install ndiswrapper 1.9 with apt-get everything goes just right until the part where I should do sudo modprobe ndiswrapper. It prompts: 
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.
``` 

I founded that the solution was or to install ndis from source or to try module assistant.

If I try to install from source the make command prompts:
```
make -C driver                            
make[1]: Entering directory `/home/axel/ndiswrapper-1.9/driver'
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/axel/ndiswrapper-1.9/driver \
                DRIVER_VERSION=1.9                                                      
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'                  
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/axel/ndiswrapper-1.9/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/axel/ndiswrapper-1.9/driver] Error 2                                                                     
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'                                                                
make[1]: *** [default] Error 2                                                                                                       
make[1]: Leaving directory `/home/axel/ndiswrapper-1.9/driver'                                                                       
make: *** [all] Error 2    
```

And I didn't found how to fix it.

If I try module-assistant it prompts:

```
Installation of the ndiswrapper-source source failed.              

Ignoring this package. Maybe you need to add something to          
sources.list, maybe the contrib and non-free archives.
```

I think that my sources.list is correct, here it is, just in case:
```
# deb cdrom:[Kubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.mirror.iweb.ca/ karmic main restricted
deb-src http://ubuntu.mirror.iweb.ca/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.mirror.iweb.ca/ karmic-updates main restricted
deb-src http://ubuntu.mirror.iweb.ca/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.mirror.iweb.ca/ karmic universe
deb-src http://ubuntu.mirror.iweb.ca/ karmic universe
deb http://ubuntu.mirror.iweb.ca/ karmic-updates universe
deb-src http://ubuntu.mirror.iweb.ca/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.mirror.iweb.ca/ karmic multiverse
deb-src http://ubuntu.mirror.iweb.ca/ karmic multiverse
deb http://ubuntu.mirror.iweb.ca/ karmic-updates multiverse
deb-src http://ubuntu.mirror.iweb.ca/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://ubuntu.mirror.iweb.ca/ karmic-security main restricted
deb-src http://ubuntu.mirror.iweb.ca/ karmic-security main restricted
deb http://ubuntu.mirror.iweb.ca/ karmic-security universe
deb-src http://ubuntu.mirror.iweb.ca/ karmic-security universe
deb http://ubuntu.mirror.iweb.ca/ karmic-security multiverse
deb-src http://ubuntu.mirror.iweb.ca/ karmic-security multiverse
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/samrog131/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/yogarine/eclipse/ubuntu karmic main
deb http://ubuntu.mirror.iweb.ca/ karmic-backports restricted main multiverse universe

```


Thanks to all!
Axel

---

### Post by blueidealist on 2009-11-11
Axel, I have the exact same issues in Ubuntu 9.10 and tried the very same things (in about 10 hours time spent on the computer in total frustration) to get the very same errors.

There never seems to be a solution that can work to the end...

Keep me posted if anything evolves on your side, will do the same.

---

### Post by Light-kun on 2011-09-30
2006... And in 2011 I got same errors when installing rt2860 drivers for eeepc901.
Any workarouds?

---

### Post by Stolgrove on 2011-10-01
it's 1 October 2011, and I havent seen anything addressing this yet. Exact same error, If I find a resolution to this I will post the link or something here also.

---

### Post by praseodym on 2011-10-01
Hi Light-kun and Stolgrove,

which devices do you use? Please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Light-kun on 2011-10-02
Hello.
Thanks for the clue, I was such an idiot =)

rfkill list showed me thst I just didn't turned on wifi hotkey on my notebook!
```
0: eeepc-wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: eeepc-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

clicked Fn+F2 and voila! 
P.S: Previously I've installed driver from RAlinktech site (make && make install && insmod rt2860sta.ko)

Lots of thanks, guys! =)

---

