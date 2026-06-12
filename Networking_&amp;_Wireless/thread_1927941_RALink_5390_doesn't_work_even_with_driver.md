---
title: "RALink 5390 doesn't work even with driver"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by nelstomlinson on 2012-02-19
My wireless does not work with Ubuntu 10.10-i386.  It does work with 11.10, but there is some kind of boot problem that leaves me with an arch independent elf magic error at boot-up, after a fresh install.  This is a 64 bit machine.

I've searched through the forum here, and installed the driver for my wireless chip.  lspci shows: 05:00.0 Network controller: RaLink Device 5390

I was able to run make and make install with no problems.  Modprobe can load the driver.  Lspci -nnk shows:

05:00.0 Network controller [0280]: RaLink Device [1814:5390]
	Subsystem: RaLink Device [1814:f051]
	Kernel driver in use: rt2860
	Kernel modules: rt5390sta

It seems that there are two drivers in use, and neither is working.  

When the rt5390sta module is installed, iwconfig reports:
ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

When the rt5390sta module is not installed, the ra0 doesn't show up.

Does anyone have any ideas to get the wireless working?  I'm at a loss.

Sorry if this all sounds confused, but I'm very confused right now.

---

### Post by praseodym on 2012-02-19
Two driver at one time do not work. Blacklist the wrong one:

```
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot or reload the right one:

```
sudo modprobe -rfv rt2800pci rt5390sta
sudo modprobe -v rt5390sta
```
Check with

```
lsmod
```

---

### Post by nelstomlinson on 2012-02-19
I was wondering if two was a problem.  I have the following lines in the /etc/modprobe.d/blacklist.conf file:
blacklist rt2800pci
blacklist rt2860

After a re-boot, lspci -nnk shows:
05:00.0 Network controller [0280]: RaLink Device [1814:5390]
	Subsystem: RaLink Device [1814:f051]
	Kernel driver in use: rt2860
	Kernel modules: rt5390sta

When I try to get rid of that, sudo modprobe -r rt2860 produces:
FATAL: Module rt2860 not found.

That rt2860 is listed as a kernel driver; maybe that's why modprobe can't find it?

---

### Post by praseodym on 2012-02-19
rt5390sta normally only is an "alias" for rt2860sta. Check:

```
modinfo rt5390sta | egrep 'versi|filen'
modinfo rt2860sta | egrep 'versi|filen'
grep rt28 /etc/modprobe.d/*
```

---

### Post by nelstomlinson on 2012-02-19
> **praseodym said:**
> rt5390sta normally only is an "alias" for rt2860sta. Check:

```
modinfo rt5390sta | egrep 'versi|filen'
modinfo rt2860sta | egrep 'versi|filen'
grep rt28 /etc/modprobe.d/*
```

Thanks, I'll check that out when I get home, and let you know what I find.  If rt2860 is the right one, I'll still have to figure out why ifconfig can't see the ralink.

---

### Post by nelstomlinson on 2012-02-19
> **praseodym said:**
> rt5390sta normally only is an "alias" for rt2860sta. Check:

```
modinfo rt5390sta | egrep 'versi|filen'
modinfo rt2860sta | egrep 'versi|filen'
grep rt28 /etc/modprobe.d/*
```


Here's what I get:
tomlinso@tomlinso-p7-1267c:~$ modinfo rt5390sta
filename:       /lib/modules/2.6.35-32-generic-pae/kernel/drivers/net/wireless/rt5390sta.ko
version:        2.5.0.1
srcversion:     A5DDD0453DFBFF7571C142D
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.35-32-generic-pae SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)

Not sure what it means.

---

### Post by praseodym on 2012-02-20
Maybe some firmware missing?! Download the package linux-firmware from [http://packages.ubuntu.com](http://packages.ubuntu.com) for 12.04, install it by double click and reboot

---

