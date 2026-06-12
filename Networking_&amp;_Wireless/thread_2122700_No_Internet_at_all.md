---
title: "No Internet at all"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by Tommy5454 on 2013-03-05
Hi all, I am brand new to Ubuntu but have been scouring these forums for two straight days to no avail. 
I have 12.10 installed on a Toshiba laptop. I just installed it but even when wired no internet connection pops up. I cannot get wireless, I cannot get wired. Even when I installed the CD while wired it said no internet connection in the install wizard. 
I have tried installing 12.04 and 11.10 but the same issue occurred with those. 

I really want to be an ubuntu guy but I cannot even get on the internet. Help?

---

### Post by papibe on 2013-03-05
Hi Tommy5454. Welcome to the forums ):P

Could you post the results of these commands?
```
lspci -nnk | grep -iA2 eth

sudo lshw -C network

ifconfig

route -n

nslookup ubuntu.com

dig ubuntuforums.org

```
Regards.

---

### Post by Tommy5454 on 2013-03-06
Hey, thanks for your response. I like your avatar I have one of those guys myself. 

> **papibe said:**
> Hi Tommy5454. Welcome to the forums ):P

Could you post the results of these commands?
```
lspci -nnk | grep -iA2 eth
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10) 
       Subsystem: Toshiba America Info Systems Device [1179:ff1e] 
02:00.0 Network controller [280]: Realtek Semiconductor Co., Ltd. Device [10ec: 8723]

sudo lshw -C network
*network UNCLAIMED
   description: Ethernet controller
   product: AR8162 Fast Ethernet
   vendor Atheros Communications Inc.
   physical id: 0
   bus info: pci@0000:01:00.0
   version: 10
   width 64 bits
   clock: 33MHz
   capabilities: pm pciexpress msi msix bus_master cap_list
   configuration: latency=0
   resources: memory:b8500000-b853ffff ioport:3000(size=128)
*-network UNCLAIMED
   description: Network controller
   product: Realtek Semiconductor Co., Ltd.
   vendor: Realtek Semiconductor Co., Ltd.
   physical id: 0
   bus info: pci@0000:02:00.0
   version: 00
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress bus_master cap_list
   configuration: latency=0
   resources: ioport:2000(size=256) memory:b8400000-b8403fff

ifconfig
   Link encap:Local Loopback
   inet addr:127.0.0.1 Mask:255.0.0.0
   inet6 address: ::1/128 Scope:Host
   UP LOOPBACK RUNNING MTU:16436 Metric:1
   RX packets: 6552 errors:0 dropped:0 overruns:0 frame:0
   TX packets: 6552 errors:0 dropped:0 overruns:0 frame:0
   collisions:0 txqueuelen:0
   RX bytes: 536096 (536.0 KB) TX bytes: 536096 (536.0 KB)

route -n
Kernel IP routing table
Destination     Gateway    Genmask    Flags Metric Ref    Use Iface

nslookup ubuntu.com
;;connection timed out; no servers could be reached

dig ubuntuforums.org

```
Regards.

---

### Post by papibe on 2013-03-06
Thanks.

Your laptop has network devices that are relatively new. I would advice installing 12.10.

**Wireless:**
[INDENT]Make sure your hardware wireless switch is ON. I have a Toshiba A665 laptop and the keyboard button to enable/disable wireless actually works.

You may need to enable it by software also. Check this [tutorial]("http://www.digimantra.com/linux/rfkill-enabledisable-wireless-linux-laptop/") on how to use 'rfkill' to do that.[/INDENT]

**Wired:**
[INDENT]Try loading manually the module 'alx', which will be available only on 12.10.[/INDENT]

Sources: [here]("http://ubuntuforums.org/showthread.php?t=2087723"), [here]("http://ubuntuforums.org/showthread.php?t=2050126"), and [here]("http://askubuntu.com/questions/205582/how-do-i-get-an-atheros-ar8162-working"). 

Let us know if you need more help with the process.
Regards.

---

### Post by Tommy5454 on 2013-03-06
Hey, thanks for all the help. I checked the hardware switch and the light shows wireless as on. So I tried the rfkill list in terminal and the only thing it lists is bluetooth:

1: hci0: Bluetooth
    Soft Blocked: no
    Hard Blocked: no

I looked at the sources you sent me but all of those seem to rely on having some sort of connection to the internet. I do have another computer (which is how I am on this forum) so I can use a USB stick to transfer patches or fixes. Reading through the sources I just can't tell which one I need being a newbie. 

I'm confused why my wired connection would not appear. I plug directly into the modem and nothing shows up.

---

### Post by papibe on 2013-03-06
Let's make a test.

Use the 12.10 installation media, and select 'Try Ubuntu' (Live).

One you get to the desktop, open a terminal and run:
```
sudo modprobe alx
```
wait a minute, and check is the module got loaded:
```
lsmod | grep -i alx
```
If it is, it should display something. If it is not, the rest won't be useful.

Then, restart your network:
```
sudo service network-manager stop

sudo service network-manager start
```
Try accessing the Internet with Firefox.

If you have access, you may install Ubuntu from the icon on the desktop.

Let us know how it goes.
Regards.

---

### Post by Tommy5454 on 2013-03-08
Hey, I am on vacation and didn't forget about you. I will try those steps on Monday. Thanks!

---

### Post by Tommy5454 on 2013-03-11
Looks like nothing happened. See below. It won't pick up anything but bluetooth and this alx is not picked up at all. AHHH!

One you get to the desktop, open a terminal and run:
 	Code:
 	
sudo modprobe alx
FATAL: Module alx not found.
 
wait a minute, and check is the module got loaded:
 	Code:
 	
lsmod | grep -i alx
nothing appears for this code

 
If it is, it should display something. If it is not, the rest won't be useful.

Then, restart your network:
 	Code:
 	
sudo service network-manager stop  sudo service network-manager start

---

### Post by Tommy5454 on 2013-03-11
I should also add, when trying the alx thing I could not get onto the internet - either wired or wireless. 

Is there a way to download everything I need onto a thumb drive from my other PC and transfer it? 

Or is it possible to use a dongle with my cell phone?

---

