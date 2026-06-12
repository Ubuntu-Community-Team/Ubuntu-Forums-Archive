---
title: "Netbook 10.10 wireless problem"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by boomer727 on 2011-04-27
Hey guys, new user to ubuntu, im looking for a bit of help. I've installed ubuntu inside windows xp, everything works fine, except i have to have my netbook on a wired connection, becuase im missing firmware for the wireless connection. i've looked through other threads that seem to have similar problems, i've done the "terminal -> sudo apt-get install b43-fwcutter" it gives me an error. I'm lucky enough to be surrounded by a few friends who are fairly experienced at ubuntu, but they're dumbfounded as well.

what am i doing wrong here? i've got to be missing something with this. there's not a wireless connection issue on xp when i boot into that. 

ahhh well any help is appreciated greatly guys, sorry if i don't get things right away, i've been using ubuntu for about... 2 hours now, but im sure i'll get used to it once this gets resolved.

thanks guys.

---

### Post by josephmills on 2011-04-27
Please go to your terminal and type in  ```
lspci -nn
``` 
```
lsmod | grep b43
``` ```
dmesg | grep b43
``` Then paste all here thanks

---

### Post by boomer727 on 2011-04-27
> **josephmills said:**
> Please go to your terminal and type in  ```
lspci -nn
```
```
lsmod | grep b43
```
 ```
dmesg | grep b43
```
 Then paste all here thanks

The first -
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile  945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile  945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller  [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  02)



The second- 
nothing comes up when i enter lsmod | grep b43  [?]




The last-
[    1.670950] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.670981] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[    9.118946] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    9.484940] Registered led device: b43-phy0::tx
[    9.485027] Registered led device: b43-phy0::rx
[    9.485094] Registered led device: b43-phy0::radio
[   18.777916] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   18.777931] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   18.777941] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  681.897399] b43-pci-bridge 0000:03:00.0: PCI INT A disabled

---

### Post by josephmills on 2011-04-27
> **boomer727 said:**
> 
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY** [14e4:4315] **(rev 01)

see the part in bold the 4315 is only partially supported 

> 
The second- 
nothing comes up when i enter lsmod | grep b43  [?]

if nothing showed up then there is no mods listed for the b43 driver 

> 

[   18.777916] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   18.777931] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   18.777941] b43-phy0 ERROR: You must go to 
As you can see the kernel is having a troubles  with the firmware of the b43 driver 

there is a couple of ways of going about this but
1st Do you have internet connection at all on the ubuntu box via ethernet cable(cat5)?

---

### Post by boomer727 on 2011-04-27
> **josephmills said:**
> see the part in bold the 4315 is only partially supported 


if nothing showed up then there is no mods listed for the b43 driver 


As you can see the kernel is having a troubles  with the firmware of the b43 driver 

there is a couple of ways of going about this but
1st Do you have internet connection at all on the ubuntu box via ethernet cable(cat5)?


Ahh, well im connected to the internet via an ethernet cable[right now anyway] if that helps.

---

### Post by josephmills on 2011-04-27
> **boomer727 said:**
> Ahh, well im connected to the internet via an ethernet cable[right now anyway] if that helps.

ok first go to system--admin-->synaptic package manager then in the search bar type in b43 four packages shoud show up please make sure that they are all removed to do this click on the green box and mark for removal after that press the apply button. when done with that post back

---

### Post by josephmills on 2011-04-27
also what kind of computer is this. Thanks

---

### Post by boomer727 on 2011-04-27
forgive me, but that would be in
->applications->system? because im not seeing anything admin in that system tab

---

### Post by boomer727 on 2011-04-27
> **josephmills said:**
> also what kind of computer is this. Thanks



Dell inspiron mini 10

---

### Post by josephmills on 2011-04-27
> **boomer727 said:**
> forgive me, but that would be in
->applications->system? because im not seeing anything admin in that system tab
admin is short for administration are you using 11.04?
so SYSTEM-->admin-->synaptic package manager

---

### Post by boomer727 on 2011-04-27
10.10

---

### Post by josephmills on 2011-04-27
> **boomer727 said:**
> 10.10

k tell me when you removed the b43 from synaptic

---

### Post by DividedSky on 2011-04-27
> **josephmills said:**
> k tell me when you removed the b43 from synaptic

im also following this thread, whats next after uninstalling the 4 b43s in synaptic?

---

### Post by josephmills on 2011-04-27
> **DividedSky said:**
> 
im also following this thread, whats next after uninstalling the 4 b43s in synaptic?



 please start new thread. Also Please go to your terminal and type in
```

lspci -nn

```
```

lsmod | grep b43

```
```

dmesg | grep b43

```
Then paste all in the new thread by the way I like the name "the trick is to surrender to the flow"

---

### Post by DividedSky on 2011-04-27
maknig new thread...

haha! another fan ;)

---

