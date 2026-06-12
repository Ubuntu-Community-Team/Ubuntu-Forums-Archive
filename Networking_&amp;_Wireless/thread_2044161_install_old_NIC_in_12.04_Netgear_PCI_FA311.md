---
title: "install old NIC in 12.04 Netgear PCI FA311"
date: 2012-08-18
forum: Networking &amp; Wireless
---

### Post by theunfrailhale on 2012-08-18
I have a fresh install of 12.04 Server and I want to install a new PCI NIC.

the NIC is a Netgear FA311, an old 10/100

I have located the etc/network/interfaces file as the location I need to modify to install it.

I added the following to the file;

...
#description...
auto eth1 natsemi
iface eth1 inet dhcp
...

auto because I want ifup to bring the interface up at boot,
eth1 because thats what I want the interface to be called,
natsemi because thats what I read online was a proper driver "callout" (?)

the rest is pretty well understood, and copied from eth0, which is fine

I tried to run the "sudo ifup -a" command like I read in the interfaces man in an attempt to bring the interface up, but it returned

"
cannot find device "eth1"
Failed to bring up eth1
ignoring unknown interface natsemi=natsemi
_
"

obviously there is something I dont understand about installing new interfaces. Please help with some knowledge or links to, I dont mind reading, but linux commands differ over time and distro and i have a hard time finding what I need via google. 

Thanks in advance
Dave

---

### Post by chili555 on 2012-08-18
> eth1 because thats what I want the interface to be called,It will be called whatever udev calls it unless you do some careful and thoughtful surgery.

Has the driver married the device and created an interface eth1?```
ifconfig
```If not, it's meaningless to declare it in /etc/network/interfaces.

If so, the file ought to be, in addition to lo:```
auto eth1 
iface eth1 inet dhcp 
```Now try again:```
sudo ifdown eth1 && sudo ifup eth1
```Any errors or warnings? Did it get an IP address?

---

### Post by theunfrailhale on 2012-08-18
I have been tinkering since the initial post, these are the things that I now know...

> Has the driver married the device and created an interface eth1?"
eth1              Link encap:Ethernet    HWaddr .....
..
"

it looks like its recognized now, but I am not sure why.

After the initial post, I rebooted, which I should've done before initial post i suppose. When I booted the machine after physically installing the card, "ifconfig" did not report the eth1 interface. after I edited the /etc/network/interfaces it did...

I want to make sure that I am properly grasping the concept for installing a new NIC, because while I have this old 10/100 card working, I may decide to grab a newer 10/100/1000 card. 

When adding a PCI network card, I would think to;
 find if additional drivers are needed, if so, place them (where?).
once drivers are on the machine, edit the /etc/network/interfaces and add the eth# and settings?

Im trying to grasp the big concept here so I have more understanding in the future. I really appreciate the response.

> Now try again:     Code:
     sudo ifdown eth1 && sudo ifup eth1 
Any errors or warnings? Did it get an IP address?     at this point, this is what I get from this command;

"ssh stop/waiting
ssh start/running, process 1435
$ _"

---

### Post by chili555 on 2012-08-18
> find if additional drivers are needed, if so, place them (where?).In the case of commonly available ethernet cards, the drivers are probably already in the kernel and in the right place. The efficient way is to install the card physically in the box. Open a terminal and look for the identifiers:```
lspci -nn | grep 0200
```Google the pci.id and see the driver needed. Here is an example from my machine:```
chili@LAPTOP60:~$ lspci -nn | grep 0200
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [[COLOR="Red"]8086:10ea[/COLOR]] (rev 06)
```When I google the pci.id, I see that the driver is e1000e. Now I see if it's already loaded:```
chili@LAPTOP60:~$ lsmod | grep e1000e
e1000e                142384  0 
```It is, so I hope I have an interface and I check:```
chili@LAPTOP60:~$ ifconfig
[COLOR="Red"]eth0[/COLOR]      Link encap:Ethernet  HWaddr xx:de:f1:3e:b2:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

```I do, so I'm ready to declare it in /etc/network/interfaces.

Your device comes in two, at least, versions; one uses natsemi and one uses 8139cp. Be sure to check as above or post back and ask me.> once drivers are on the machine, edit the /etc/network/interfaces and add the eth# and settings?Exactly!

---

### Post by theunfrailhale on 2012-08-18
the thorough response is much appreciated, Im learning a great deal.

the output of the recommended command is as follows;

```

.../$ lspci -nn | grep 0200
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
04:02.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
```[COLOR=Red][COLOR=Black]
[/COLOR][/COLOR] 
i figured "100b:0020" was my pci.id but google didnt give much helpful info with just that info.

I did find in my search to verify that *was* the pci.id of my card, a database of pci.ids
[http://pciids.sourceforge.net/v2.2/pci.ids](http://pciids.sourceforge.net/v2.2/pci.ids)

> [COLOR=DarkOrange]100b[/COLOR]  National Semiconductor Corporation
         0001  DP83810
 ...
         [COLOR=DarkOrange]0020[/COLOR]  DP83815 (MacPhyter) Ethernet Controller
                103c 0024  Pavilion ze4400 builtin Network
                12d9 000c  Aculab E1/T1 PMXc cPCI carrier card
                [COLOR=DarkOrange]1385[/COLOR] f311  [COLOR=DarkOrange]FA311[/COLOR] / FA312 (FA311 with WoL HW)I think I am catching on here, and your posts have been key to my understanding, so thanks again!

it would seem that 0200 is a generic hardware type identifier, and it seems it would serve me to know others so I will see what google turns up on that regard.

please confirm that i did indeed get the syntax right in the /etc/networking/interfaces file.
do I need to add "natsemi" after auto eth1? or since the driver is already contained in the kernel is this a useless callout? if it was not in the kernel, where would I call it out in /interfaces? do I need to, or do I just place the related drivers in the proper location?

and how do I give karmic thanks for your responses? is there rep points? i know it could be considered trivial to track such, but I really appreciate the info.

---

### Post by chili555 on 2012-08-19
> 04:02.0 Ethernet controller [0200]: [COLOR="Red"]Nat[/COLOR]ional [COLOR="Red"]Semi[/COLOR]conductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]The first step I'd take, even before Google, is to test for the most likely driver by looking in the alias fields for your device:```
chili@LAPTOP60:~$ modinfo natsemi | grep 0020
alias:          pci:v0000[COLOR="Red"]100B[/COLOR]d0000[COLOR="Red"]0020[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v0000100Bd00000020sv000012D9sd0000000Cbc*sc*i*
```A Google search finds this: [http://cateee.net/lkddb/web-lkddb/NATSEMI.html](http://cateee.net/lkddb/web-lkddb/NATSEMI.html)> modules built: natsemi, natsemi
<snip>
lkddb pci [COLOR="Red"]100b 0020[/COLOR] .... .... ...... : CONFIG_NATSEMI : drivers/net/natsemi.cOrdinarily, as the computer boots and PCI and USB devices are found, their vendor ID (100b in this case) and product ID (0020 in this case) are matched against the alias fields of all modules and, if found, the driver loaded. Ordinarily, the process is automatic and accurate and requires no human intervention. Didn't natsemi load all by itself?```
lsmod | grep natsemi
```> please confirm that i did indeed get the syntax right in the /etc/networking/interfaces file.
do I need to add "natsemi" after auto eth1? No on both counts. It's needless and just confuses the system. My syntax is correct.

If the module didn't load automagically, the correct procedure is to add it to /etc/modules:> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
natsemi> but I really appreciate the info.That's all the points I need. Thanks.

---

