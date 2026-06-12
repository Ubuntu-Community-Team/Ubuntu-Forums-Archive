---
title: "how to enable wireless?"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by psobreira on 2010-07-21
[COLOR=#000000]I have a LG S1 PRO,  that to activate the wireless is necessary Fn + F6.

[/COLOR]How do I enable  wireless on command? Since you can not activate in ubuntu with these keys.

Someone can help  ...

[COLOR=#000000]thanks[/COLOR]

---

### Post by pytheas22 on 2010-07-21
You can enable wireless from the command line with:
```

sudo rfkill unblock all
```

But usually the hotkeys work, so if Fn+F6 is not doing anything, it may indicate a deeper problem.  If the rfkill command doesn't enable the wireless either, please post the output of these commands to help identify what's wrong:
```

lshw -C Network
lspci -nn
lsusb
rfkill list all
dmesg | grep -ie radio -e wlan
```

You should also check in your BIOS to see if there are settings related to the wireless being turned on or off; sometimes playing with these is necessary to get the function keys working properly.

---

### Post by psobreira on 2010-07-22
This option does not result.
```
sudo rfkill unblock all
```

In the  BIOS there is no option on wireless.

```

pedro@pedro-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: ET-131x PCI-E Ethernet Controller
       vendor: Agere Systems
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:91:10:d8:90
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=et131x ip=192.168.10.7 latency=0 multicast=yes
       resources: irq:16 memory:d4000000-d41fffff memory:d0000000-d001ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:d2:17:8c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:d8100000-d8100fff

```
```

pedro@pedro-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M56P [Radeon Mobility X1600] [1002:71c5]
02:00.0 Ethernet controller [0200]: Agere Systems ET-131x PCI-E Ethernet Controller [11c1:ed00] (rev 02)
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
06:00.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
06:00.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
06:00.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
06:00.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]

```
```
pedro@pedro-laptop:~$ lsusb
Bus 005 Device 003: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 005 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 043e:9802 LG Electronics USA, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
pedro@pedro-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
```
pedro@pedro-laptop:~$ dmesg | grep -ie radio -e wlan
[   18.014395] iwl3945 0000:05:00.0: Radio disabled by HW RF Kill switch
[   18.028703] iwl3945 0000:05:00.0: Radio disabled by HW RF Kill switch

```
[COLOR=#000000]thanks for your help[/COLOR]

---

### Post by pytheas22 on 2010-07-22
Thanks for the output.  It's definitely the hardware switch that's at fault.

Maybe this is a dumb question, but I assume you've at least tried turning on the wireless with Fn+F6?  And you're positive there's absolutely no other switch that needs to be on to make the wireless work?  I ask only because everything else in your output indicates that these keys simply need to be pressed.

---

### Post by somanybears on 2010-07-22
What does Fn-F6 do? 

I am having the exact same problem as psobreira! I feel your pain

---

### Post by psobreira on 2010-07-22
Yes, the problem  is that the hardware switch. This laptop Fn + F6  is the only way on / off the wireless. In  windows by pressing Fn + F6 opens a popup on/off the wireless and  bluetooth, but as for Linux software that does not exist, there must be  another way, but what ....??

Yes I've tried  pressing Fn + F6 ... but unfortunately did not  work. Why not to press the wireless connect or  disconnect it on windows is done by software and just have it installed  you can enable wireless, pressing Fn + F6 just do not open the popup is  to enable wireless on windows clear.

Thanks  for your help ... I enter the world of Ubuntu,  but without wireless it is very difficult ... impossible ...

---

### Post by pytheas22 on 2010-07-22
Could you please try booting to Windows, enabling the wireless there, and then (with the wireless still enabled) reboot directly into Ubuntu?  After that, can you scan for wireless networks in Ubuntu by typing:
```

sudo iwlist scan
```

or using the NetworkManager applet in the upper-right corner?

It's possible that Ubuntu can't turn the wireless on, but that if you turn it on in Windows, it will remain enabled when you boot into Ubuntu.

---

### Post by psobreira on 2010-07-23
The option in the right corner superiror is disabled.
 
Now I do not have windows installed on the laptop, only ubuntu ...

---

### Post by psobreira on 2010-07-23
the problem is the same for activation of hardware... I can not activate the wirelles with the command *sudo rfkill unblock 0*

```
pedro@pedro-laptop:/$ sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```But there must be some command to activate it ...

Can someone help...

---

### Post by pytheas22 on 2010-07-23
Sorry to ask again, but you're positive there's no option in BIOS relating to the wireless?  There might not necessarily be a choice for forcing it on or off, but there might be other options; if there are, please let us know.

Another thing that can sometimes help is shutting the laptop down completely (not just suspending or hibernating), unplugging the power cord and the battery and then holding in the power button for about a minute.  This will cut off all electricity, which should force your hardware to reset.  If Windows left your wireless card in a state where only Windows can wake it back up, this should fix it, with any luck.

---

### Post by peyek on 2010-08-06
I also have the same problem with [psobreira]("http://ubuntuforums.org/member.php?u=1116276") anyone help?

---

### Post by pytheas22 on 2010-08-10
**peyek and allisonays**: there are many different possible causes of the problem and you can't be certain that your issues are the same as psobreira's.  If you could please post the output of these commands, I'll try to help you:
```

lspci -nn
lsusb
sudo iwlist scan
dmesg | grep -e wlan -ie radio
rfkill list all
```

---

