---
title: "Wire lan azdapter not recognised PLEASE HELP !!!"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by basilwatson on 2010-10-06
I have tried 2 usb adapters in order to get internet to this computer with ABSOLUTELY NO LUCK 

this is ubuntu 10 .04 LTS  64 bit 

and the usb adapter is;  logitec corp Lan w150 n u2  0789:0168

tried every thing I coul , blacklisted the pci card , ndiswrapper , and while it will pick up the usb , there is NO WLAN 

here are the outputs 
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Open a socket for LPF: Operation not permitted


s@s-desktop:~$ sudo ifup wlan
[sudo] password for s: 
Ignoring unknown interface wlan=wlan.

interfaces

auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet dcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp



s@s-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 192f:0416 Avago Technologies, Pte. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 003: ID 0789:0168 Logitec Corp.** 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

s@s-desktop:~$ ndiswrapper -l
net8192su : driver installed

s@s-desktop:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
[sudo] password for s: 
ndiswrapper
s@s-desktop:~$ 
s@s-desktop:~$ dmesg | grep -e ndis -e wlan
[   18.403767] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   19.121627] usbcore: registered new interface driver ndiswrapper
s@s-desktop:~$ 


s@s-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:45:e7:f1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.3 latency=0 multicast=yes
       resources: irq:28 ioport:b800(size=256) memory:ffdff000-ffdfffff memory:ffdc0000-ffddffff(prefetchable)
s@s-desktop:~$ 



When I black list this , I get description . or network I cant remember I get unclaimed , ala the wiki , but I can get anything to work after that 

Please someone give us a hand this is ridiculous 

Kind regards 

Stephen

---

### Post by basilwatson on 2010-10-07
bump

---

### Post by basilwatson on 2010-10-07
bump

---

### Post by basilwatson on 2010-10-07
Sorry p@osting it here as no joy in networking section , and I REALLY need this to work , as My workshop is without internet and I am not running thirty meters of lan cable 

Please would some kind soul , take pity 

Snip;

Wire lan azdapter not recognised PLEASE HELP !!!
I have tried 2 usb adapters in order to get internet to this computer with ABSOLUTELY NO LUCK

this is ubuntu 10 .04 LTS 64 bit

and the usb adapter is; logitec corp Lan w150 n u2 0789:0168

tried every thing I coul , blacklisted the pci card , ndiswrapper , and while it will pick up the usb , there is NO WLAN

here are the outputs
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Open a socket for LPF: Operation not permitted


s@s-desktop:~$ sudo ifup wlan
[sudo] password for s:
Ignoring unknown interface wlan=wlan.

interfaces

auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet dcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp



s@s-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 192f:0416 Avago Technologies, Pte.
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0789:0168 Logitec Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

s@s-desktop:~$ ndiswrapper -l
net8192su : driver installed

s@s-desktop:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
[sudo] password for s:
ndiswrapper
s@s-desktop:~$
s@s-desktop:~$ dmesg | grep -e ndis -e wlan
[ 18.403767] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 19.121627] usbcore: registered new interface driver ndiswrapper
s@s-desktop:~$


s@s-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 01
serial: 00:1a:92:45:e7:f1
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list rom ethernet physical
configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.3 latency=0 multicast=yes
resources: irq:28 ioport:b800(size=256) memory:ffdff000-ffdfffff memory:ffdc0000-ffddffff(prefetchable)
s@s-desktop:~$



When I black list this , I get description . or network I cant remember I get unclaimed , ala the wiki , but I can get anything to work after that

Please someone give us a hand this is ridiculous

Kind regards

Stephen

---

### Post by basilwatson on 2010-10-07
last bump

---

### Post by basilwatson on 2010-10-07
bump

---

### Post by basilwatson on 2010-10-07
come on isn't ANYONE going to help ?

---

### Post by basilwatson on 2010-10-07
bump

---

### Post by Merthod on 2010-10-07
Could you paste the output of [FONT="Courier New"]ifconfig[/FONT] for wlan0 please?

---

### Post by basilwatson on 2010-10-07
> **Merthod said:**
> Could you paste the output of [FONT="Courier New"]ifconfig[/FONT] for wlan0 please?

s@s-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:199550 (199.5 KB)  TX bytes:199550 (199.5 KB)


thanks for the help , I've manage to kill the wired connection now !!!

I will post an system up date because i have been blindly fiddling , using scraps of info from the Internet 

s@s-desktop:~$ uname -m
x86_64

s@s-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:199550 (199.5 KB)  TX bytes:199550 (199.5 KB)

s@s-desktop:~$ sudo ifup wlan
[sudo] password for s: 
Ignoring unknown interface wlan=wlan.
s@s-desktop:~$ ndiswrapper -l
autorun : invalid driver!
s@s-desktop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:b800(size=256) memory:ffdff000-ffdfffff memory:ffdc0000-ffddffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

s@s-desktop:~$ dmesg | ndis -e wlan
No command 'ndis' found, did you mean:
 Command 'gdis' from package 'gdis' (universe)
ndis: command not found



s@s-desktop:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
s@s-desktop:~$ dmesg | ndis -e wlan
No command 'ndis' found, did you mean:
 Command 'gdis' from package 'gdis' (universe)
ndis: command not found
s@s-desktop:~$ 




Stephen

---

### Post by Merthod on 2010-10-07
This is a similar task they managed to get working, check it out to see if it applies to you:

[http://www.alstevens.co.uk/how-to-install-wireless-usb-drivers-for-ubuntu/]("http://www.alstevens.co.uk/how-to-install-wireless-usb-drivers-for-ubuntu/")

To bring alive your wired connection you may use [FONT="Courier New"]sudo ifconfig eth0 up[/FONT]. See [FONT="Courier New"]man ifconfig[/FONT] for more information.

A note of caution: when you alter your configurations you may screw up your system. So if you tried something and it didn't work, undo it.

Hope this helps.

---

### Post by basilwatson on 2010-10-08
The problem is I cant extract the driver from the exe file 

I found a driver , pretty sure its the one for the card , aand I will try that again ( my net book works well as I am in the workshop now using it ) 

thanks for the help 

Stephen

and I have just tried the cd that came with it and I cant find an .inf file anywhere on it, will download another and try again

---

### Post by Merthod on 2010-10-08
you might contact logitech support for a non-exe driver package, maybe a zip?

---

### Post by basilwatson on 2010-10-08
> **Merthod said:**
> you might contact logitech support for a non-exe driver package, maybe a zip?

joined a dodgy site downloaded a few drivers 

my gosh this is Micky mouse , really is 

Stephen

---

### Post by basilwatson on 2010-10-08
I dont know I rtried every realteck RtL8,,, driver I could think of 


my only options are buy another adapter 

contact logitech , for a non helpful answer 

or dig 30 foot of trenching and lay Lan cable  ( which is SERIOUSLY MICKY MOUSE  ) 

the last option is looking the best ......

thanks Merthod for your help , 

Kind Regards Stephen

---

### Post by lisati on 2010-10-08
Threads merged. Please do not post multiple threads on the same question: see item 12 in the "Posting tips" section of the [forum code of conduct]("http://ubuntuforums.org/index.php?page=policy").

---

### Post by KiwiNZ on 2010-10-08
@ OP you have been multiple posting , impatiently bumping a thread multiple times in  24  hour period. 

Volunteers are not here waiting for you to post and instantly fix your issues, that is not how a community run support unit runs.

Good luck with your efforts , I am closing this thread.

---

