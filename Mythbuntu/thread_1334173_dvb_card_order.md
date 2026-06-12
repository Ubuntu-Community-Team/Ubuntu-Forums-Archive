---
title: "dvb card order"
date: 2009-11-22
forum: Mythbuntu
---

### Post by Crowie on 2009-11-22
Hi since upgrading to mythbuntu 9.10 my dvb cards keep changing order 

from a cold boot on my mythbox the order of the cards are:
dvb:0 dvb-s tuner Kworld cx88 driver
dvb:1 dvb-t nova-t usb 
dvb:2 Nova-t PCI cx88 driver

I then Reboot and the order is

dvb:0   DVB-T usb
dvb:1   dvb-s pci
dvb:2   dvb-t nova-t pci

and stays like this after every reboot until machine is powered off.

```
dmesg | grep -i registering
[    8.492788] DVB: registering new adapter (Hauppauge WinTV-NOVA-T usb2)
[    8.497149] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
[   11.002918] cx88/2: registering cx8802 driver, type: dvb access: shared
[   11.266086] DVB: registering new adapter (cx88[0])
[   11.266090] DVB: registering adapter 1 frontend 0 (Conexant CX24123/CX24109)...
[   11.519352] DVB: registering new adapter (cx88[1])
[   11.519357] DVB: registering adapter 2 frontend 0 (Conexant CX22702 DVB-T) 
```

My question is what method are people using to force there dvb cards to be allocated in a particular order.

I have had a look at adding to /etc/modprobe.d/options-dvb.conf but kworld dvb-s appears to share same driver as the nova-t pci card

really i only need to force the dvb-s card to be loaded first as this uses a different video source.  The other dvb-t cards can start in any order after.   

TIA

---

### Post by ian dobson on 2009-11-22
Hi,

Maybe you could use udev rules to create symbolic links from the real device names to names that don't change on reboot:-

/dev/dvbs always points to the dvb-s tuner
/dev/dvbt0 always points to the first dvb-t tuner

See this thread for some more information. 
[http://ubuntuforums.org/archive/index.php/t-542903.html](http://ubuntuforums.org/archive/index.php/t-542903.html)

There's also a thread somewhere in this forum on how to use python and udev rules to create hardwired device names for dvb tuners, but at the moment I can't find it.

Regards
Ian Dobson

---

### Post by Neon Dusk on 2009-11-22
If they're using the same module then I think you'll need to create udev rules.
There's a udev-rules-jaunty.py script [thread=753434]here[/thread] - although I'm not sure if this works for DVB cards. 

In the past I've used 
```

udevadm info -a -p $(udevadm info -q path -n /dev/dvb/adapter0/frontend0)
udevadm info -a -p $(udevadm info -q path -n /dev/dvb/adapter1/frontend0)

```

To compare the differences to between the cards then created a udev rule :-

```

# /etc/udev/rules.d/10-local.rules
# 
# To Identify serial nos etc for a Device use
# udevadm info -a -p $(udevadm info -q path -n /dev/dvb/adapter0/frontend0)
# 
# Creates an adapter100 link for the Nova card & adapter101 link for the Twinhan card

#Nova HD S2 - DVS-S2
SUBSYSTEM=="dvb", KERNELS=="0000:01:06.2", DRIVERS=="cx88-mpeg driver manager", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter100/%%s $${K#*.}'", SYMLINK+="%c"

#Twinhan - DVB-T
SUBSYSTEM=="dvb", ATTRS{manufacturer}=="TWINHAN", ATTRS{product}=="VP-7045", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter101/%%s $${K#*.}'", SYMLINK+="%c"


```

---

### Post by ian dobson on 2009-11-22
Hi,

OK you beat me too it. The link I have is [http://ubuntuforums.org/showthread.php?t=1070912&highlight=udev+pvr150](http://ubuntuforums.org/showthread.php?t=1070912&highlight=udev+pvr150)

Regards
Ian Dobson

---

### Post by pootle1 on 2009-11-22
you may find this thread an easier option...
[http://ubuntuforums.org/showthread.php?t=1311795](http://ubuntuforums.org/showthread.php?t=1311795)

---

### Post by Crowie on 2009-11-22
cool I missed a trick there with udev.  Ive created a /etc/udev/rules.d/10-local.rules and initially set my dvb-s card as follows


```
# rules to allocate dvb-s card first.  Other two dvb-t cards can go in any order for the time 221109

SUBSYSTEM=="dvb", KERNELS=="0000:01:06.2", DRIVERS=="cx88-mpeg driver manager", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter100/%%s $${K#*.}'", SYMLINK+="%c"
 
```

which puts dvb-s card as /dev/dvb/adaptor100 and ive assigned this card in mythtv to this location.  It also displays the adaptor1 but I guess thats fine as the adaptor100 is just a symlink 

```
 ls -la  /dev/dvb/
total 0
drwxr-xr-x  6 root root  120 2009-11-22 17:24 .
drwxr-xr-x 18 root root 4020 2009-11-22 17:24 ..
drwxr-xr-x  2 root root  120 2009-11-22 17:23 adapter0
drwxr-xr-x  2 root root  120 2009-11-22 17:24 adapter1
drwxr-xr-x  2 root root  120 2009-11-22 17:24 adapter100
drwxr-xr-x  2 root root  120 2009-11-22 17:24 adapter2

```

@pootle1 thanks, that was my preferd method however, my dvb-s card and one of my dvb-t cards uses the same cx88 module and I couldnt get it to work.

Thanks for the help everyone

---

