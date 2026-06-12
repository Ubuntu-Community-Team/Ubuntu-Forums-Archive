---
title: "[ERR] problems with uninstalled network cards"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by mod_zero on 2010-03-20
hi@all

i'm working with computers now for more than 10years...

since a few years, i've set up my own ubuntu server ... 
but my linux knowledge is not as big as i'd like

about a year ago i've changed some network cards because of malfunction

now here comes the problem:[INDENT]root@xxx: ifconfig /all
/all: error fetching interface information: Device not found
[/INDENT]so the system believes that this 2 cards are installed till now, but they aren't ...
the loaded kernel modules are:
8139too
8139cp
3c59x
mii

so i decided to set them on the modules blacklist - that they won't be loaded anymore

but that doesn't work ... "ifconfig /all" doesn't work til now ...

and on booting up i get the following output/errors:[INDENT]8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
8139cp 0000:00:0a.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
8139cp 0000:00:0a.0: Try the "8139too" driver instead

3c59x: Donald Becker and others.
0000:00:0d.0: 3Com PCI 3c905C Tornado at f883c000.
[/INDENT]but i've set the following modules on the blacklist in /etc/modprobe.d/blacklist:[INDENT]8139too
8139cp
3c59x
[/INDENT]so my final question is:

how can i "uninstall" the not (anymore) installed network cards in ubuntu?

i just wanna know how to fully uninstall the old cards 


finally, 
thanks
zer0

---

### Post by chili555 on 2010-03-20
You seem like a fairly advanced user, so I am going to hit the high points and trust that you can accomplish this without step-by-steps. First, I'd check *lshw -C network* to be certain what module your current ethernet card is using and that it is not either of the ones quoted. Next, check */etc/modules* to see that these modules are not being explicitly loaded. Then, clean up */etc/udev/rules.d/70-persistent-net.rules* to remove any reference to cards that are no longer used and that you are confident will not be used. Amend files as needed.

If all of this does not work, amend */etc/rc.local* to rmmod -f your_module.

Please post back with any questions.

---

### Post by mod_zero on 2010-03-22
first of all - thanks 4 your help

damnit .. it seems as i'm not as advanced as i thought

for real, i had those 2 cards installed, one with an realtek 8139 chipset, and the other one was the 3Com 3c95x tornado

the i removed the older one with the 8139 chipset - and changed it by a netgear card with the same chipset...

but for the netgear card is a better module called "natsemi" - but if i would load it - it's not used by a device

so know i know i have the correct cards plugged in 

but **how can i remove the error on bootting up with the "false" module 8139cp** 

and **how can i remove the error on "ifconfig /all"** ... with lspci or lshw -C net there aren't more than 2 cards installed ... and in /etc/network/interfaces they are pretty well configured .. so if i plug in a patch-cable they both do their work 

maybe you need some information about - just ask

thanks a lot,
zer0

---

### Post by chili555 on 2010-03-22
Let's see:```
ifconfig
lspci -nn
```The addition of the incorrect module 8139cp is, in most cases, harmeless. Does the network interface work as expected? If so, I wouldn't worry about it.> root@xxx: ifconfig /all
/all: error fetching interface information: Device not foundThis just means that the syntax is incorrect. 'ifconfig' has no modifier named /all so the command thought maybe you were looking for an interface named /all. If you want to see a listing of *all* of the available interfaces, the correct syntax is, simply:```
ifconfig
```Here is a sample from my computer:> chili@LAPTOP40:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 99:0d:60:39:f5:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 99:16:6f:9a:5f:99
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe9a:5fdf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4002 errors:1 dropped:1 overruns:0 frame:0
          TX packets:2906 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3367425 (3.3 MB)  TX bytes:587497 (587.4 KB)
          Interrupt:11 Base address:0x4000 Memory:c0210000-c0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by mod_zero on 2010-03-22
both network cards do their work fine 

the "bug" with "ifconfig /all" was such a ******** - that only works under windoof with ipconfig - my fault

thanks a lot for your help - i'll keep it in mind
lg zer0

---

### Post by chili555 on 2010-03-22
Post back any time we can help you. Glad it's all working.

---

