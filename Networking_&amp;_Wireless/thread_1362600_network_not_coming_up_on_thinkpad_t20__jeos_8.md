---
title: "network not coming up on thinkpad t20  jeos 8"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by timnixon on 2009-12-23
I installed Jeos 8.04 (not desktop) on an old thinkpad. Durring install it finds the network adaptor (internal, wired). After reboot it's not there. ifconfig eth0 up returns "error while getting device interface flags:no such device". I tried disabling apci in favor of apm as seen elsewhere but it didn't help.
 
Also the same happens for my wireless card if I insert it.. and do ifconfig eth1 up
 
Any suggestions?

---

### Post by chili555 on 2009-12-23
It seems you have the famous 3Com ethernet card. Verify with:```
lspci | grep Ethernet
```If so, please check here: [http://www.thinkwiki.org/wiki/Problem_with_3Com_10/100_Ethernet_card_not_being_recognized](http://www.thinkwiki.org/wiki/Problem_with_3Com_10/100_Ethernet_card_not_being_recognized)

Have you tried the other fixes suggested here:> Try one of the following kernel parameters (in that order):

    * nolapic (disables support for local apic)
    * acpi=nopci (disables PCI resource control of the ACPI subsystem)
    * acpi=off (completely disables ACPI, should always work) If none of these work, there are other suggestions mentioned. 

I am interested to read that it says the issue was fixed for kernels after 2.6.14-rc1. What version does Jeos 8.04 run?```
uname -r
```Post back and let us know your progress.

---

### Post by timnixon on 2009-12-23
thanks, will try in the next day or so.. and yes  3com  will get back to you

---

### Post by chili555 on 2009-12-23
> I am interested to read that it says the issue was fixed for kernels after 2.6.14-rc1.My further research says that JeOS 8.04 runs 2.6.24; it should be fixed. I wonder if the correct module is just not getting loaded. Please try:```
sudo rmmod 3c59x && sudo modprobe 3c59x
ifconfig
```Does the interface now appear? If so, we can add this to rc.local.

---

### Post by timnixon on 2009-12-23
those kernel options didn't help.. I dont have perl installed or anything else since I cannot connect ;)  (chicken and egg) so I couldn't try the other possibilities
 
uname -r
2.6.24-24-virtual

---

### Post by timnixon on 2009-12-23
rmmod 3c59x returns 3c59x does not exist in /proc/modules 
... modprobe 3c59x returns 3c59x not found
 
The adapter shows as a **3Com** Corporation **3c556B** CardBus [Tornado] at installation time

---

### Post by chili555 on 2009-12-23
Hmmmm, weird. I was going by this: [http://www.thinkwiki.org/wiki/3Com_10/100_Ethernet_Mini-PCI_Adapter_with_56K_Modem](http://www.thinkwiki.org/wiki/3Com_10/100_Ethernet_Mini-PCI_Adapter_with_56K_Modem)

Especially:>     *  Chipset: [COLOR="Red"]3Com 3c556b[/COLOR]
    * PCI ID: 10b7:6056 or 10b7:6055
    * Speeds: Full-duplex 10/100 and this:> This card will work with the standard '[COLOR="Red"]3c59x[/COLOR]' Linux driver as part of any recent 2.4 or 2.6 kernelPlease let us see:```
lspci -nn | grep Ether
sudo updatedb
locate 3c5 | grep .ko
```Thanks.

---

### Post by timnixon on 2009-12-24
lspci|grep -i ether
00:03.0 Ethernet controller 3Com Corp. 3c556B cardbus [tornado] [10b7:6056](rev 20)
 
sudo updatedb 
command not found
sudo locate 
command not found
 
(find command does not find these)

---

### Post by chili555 on 2009-12-24
Please see here: [http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)

I was especially interested in this:> an efficient variant of our server operating system, configured specifically for virtual appliances. Are you running this in a virtual machine?> Without unnecessary drivers, and only the minimal required packages, ISVs can configure their supporting OS exactly as they want.It seems that '3c59x', 'updatedb' and 'locate' have been omitted, as well, probably, a great many other things.

I am no expert on virtual machines, but doesn't the virtual machine get it's networking, sound, display, etc. from the host machine?

---

### Post by timnixon on 2009-12-24
The weird part is that this OS runs great including networking on 3 other machines, just not my thinkpad.. must be something specific to that machine.
 
No it's not a VM that's running..
 
Maybe ther's an alternative text mode, small-ish ubuntu I should try instead?
 
The requirements (mine) would be this.. text mode, fast startup, networking..
 
I want to create a simple LAMP setup.. I know thers a package for it I can install, so I want the OS really.
 
Thanks for any recommendations
 
Thanks

---

### Post by chili555 on 2009-12-24
Please see: [https://help.ubuntu.com/9.04/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/9.04/installation-guide/i386/minimum-hardware-reqts.html) 

I suggest the 32-bit version of Ubuntu Server.

---

### Post by timnixon on 2009-12-28
thank you, the ubuntu server is exactly what I wanted.
The built in ethernet is fine.
 
I tried the wireless card I have (linksys WPC-11  also old) and I can only enable it by inserting it after boot up and then starting wlan0 (actually it was setup as eth1).
 
I tried the 3 kernel options but they don't help with wireless. I'll search the forums to see if there's anything posted.. meanwhile I can run with wired, but I'd prefer wireless too.
 
Thanks again

---

### Post by jonathan3087 on 2010-04-12
> **chili555 said:**
> It seems you have the famous 3Com ethernet card. Verify with:```
lspci | grep Ethernet
```If so, please check here: [http://www.thinkwiki.org/wiki/Problem_with_3Com_10/100_Ethernet_card_not_being_recognized](http://www.thinkwiki.org/wiki/Problem_with_3Com_10/100_Ethernet_card_not_being_recognized)

Have you tried the other fixes suggested here:If none of these work, there are other suggestions mentioned. 

I am interested to read that it says the issue was fixed for kernels after 2.6.14-rc1. What version does Jeos 8.04 run?```
uname -r
```Post back and let us know your progress.

Hi, having a similar issue and want to try the kernel parameters listed above.  Where/how do I change or set these?

Thanks,
jonathan

---

### Post by chili555 on 2010-04-12
> **jonathan3087 said:**
> Hi, having a similar issue and want to try the kernel parameters listed above.  Where/how do I change or set these?

Thanks,
jonathanThis was supposed to be fixed ages ago. What kernel are you running?```
uname -r
```What does this tell us?```
sudo rmmod 3c59x && sudo modprobe 3c59x
ifconfig
```Thanks.

---

### Post by jonathan3087 on 2010-04-12
uname -r gives:
2.6.31-14-generic

sudo rmmod 3c59x && modprobe 3c59x
ERROR: Module 3c59x does not exist in /proc/modules

ifconfig
lo

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

---

### Post by chili555 on 2010-04-13
Here is a post that describes the method to use a boot parameter: [http://ubuntuforums.org/showpost.php?p=9102317&postcount=6](http://ubuntuforums.org/showpost.php?p=9102317&postcount=6)

Please post back if you need further assistance.

---

