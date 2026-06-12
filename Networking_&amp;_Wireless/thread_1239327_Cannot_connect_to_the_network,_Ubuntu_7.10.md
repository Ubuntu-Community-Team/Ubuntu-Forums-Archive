---
title: "Cannot connect to the network, Ubuntu 7.10"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by masraha on 2009-08-13
i just freshly install Ubuntu 7.10 64 bit, when it complete i reboot, but got the problem with network, getting worse i cant see my network device in network tools.
i'm totally new with ubuntu (dont even know the command), please help me.

thanks in advance.

---

### Post by arch0njw on 2009-08-13
> **masraha said:**
> i just wanna make new thread, but i saw this thread so i decided to post my problem here.

i just freshly install Ubuntu 7.10 64 bit, when it complete i reboot, but got the problem with network, getting worse i cant see my network device in network tools.
i'm totally new with ubuntu (dont even know the command), please help me.

thanks in advance.

Please post the results of the following commands:

```
ifconfig -a
```

```
lspci | grep -i network
lsusb | grep -i network
```

---

### Post by masraha on 2009-08-13
ifconfig -a :

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lspci/lsusb : nothing coming up.

---

### Post by arch0njw on 2009-08-13
> **masraha said:**
> ifconfig -a :

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lspci/lsusb : nothing coming up.

Hmm... how about just "lspci".  I am first trying to make sure your system recognizes that you have a network card

Can you also post the contents of [FONT=Courier New]/etc/network/interfaces[/FONT], please?

---

### Post by masraha on 2009-08-13
lspci :
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4357 (rev 12)

```

/etc/network/interfaces :
```
auto lo
iface lo inet loopback

```

i don't know, when i'm at windows my network work fine.

---

### Post by bapoumba on 2009-08-13
Moved to its own thread.

---

### Post by masraha on 2009-08-13
thanks for making it's own thread.

anyway, i just realize that from this 
```
01:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4357 (rev 12)
```
the Ubuntu cannot detect my network device that suppose to be Generic Marvell Yukon 88E8042 PCI-E Fast Ethernet Controller.

how to make the Ubuntu recognize my network device? did it need any driver or something that i must install?

---

### Post by arch0njw on 2009-08-13
> **masraha said:**
> thanks for making it's own thread.

anyway, i just realize that from this 
```
01:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4357 (rev 12)
```the Ubuntu cannot detect my network device that suppose to be Generic Marvell Yukon 88E8042 PCI-E Fast Ethernet Controller.

how to make the Ubuntu recognize my network device? did it need any driver or something that i must install?

try adding these lines to your /etc/network/interfaces:

```
auto eth0
iface eth0 inet dhcp
```

(gksudo gedit /etc/network/interfaces)

Then restart networking from the command-line:  sudo /etc/init.d/networking restart

---

### Post by masraha on 2009-08-13
this is the modified interfaces :
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

```here is after restarting the network
```
raha@zombie-land:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
eth0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
                                                                         [ OK ]
raha@zombie-land:~$ 


```

---

### Post by bapoumba on 2009-08-14
@ masraha: I beleive this is a bug in the Gutsy kernel that has been solved with Hardy. Why did you install Gusty? It's reached end of life and is not supported any longer (no security fixes). It would be better, imho, that you run a supported Ubuntu release.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/135316](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/135316)

To make sure you are running Gutsy 7.10:
```
uname -a
lsb_release -a
```

---

### Post by arch0njw on 2009-08-14
I am at the end of my knowledge here.  I recommend commenting or removing those two lines from the interfaces file.  As pointed out by another reply, it looks like you might be victim to a known bug.  Personally, I always dislike the "upgrade" answer, but you might have no choice in this case.

Sorry I couldn't be of more help.

---

### Post by masraha on 2009-08-16
I'm really sorry for bothering you.
And thanks for your effort to try to help me. I apreciate that.

as your suggestion to upgrade the version, so i download the 9.04 version. Thanks God it finished (take almost 2 days to download it... :D).
then i install it.
Just finish the installation and Vhollaaa .... the network connection work very well (i think better than the windows one:guitar:). I post this one from the Ubuntu.
thank you very much.

---

### Post by arch0njw on 2009-08-17
Great!  Glad to hear that worked for you!  9.04 is so much better than 7.10 too.

---

### Post by bapoumba on 2009-08-18
Congrats masraha, glad to see you go tit to work :)

---

