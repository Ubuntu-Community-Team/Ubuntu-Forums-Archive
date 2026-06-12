---
title: "wireless card drivers not working"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by Clean1414 on 2008-12-28
im trying to make the wireless-G PCI Adapter WG311v3 to work with ubuntu 8.10 x64. ive been reading two forms to get this card working, i read both [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3) and [http://ubuntuforums.org/showthread.php?t=320111](http://ubuntuforums.org/showthread.php?t=320111) when i installed the drivers according to both these sources, instead of getting it working when using the "ndiswrapper -l" command to see if its working it gives me this instead "invalid driver!" what can i do to get this card working, and if its easier to buy a new card that works native with ubuntu 8.10 x64 that is under 40 please give me a link to such a card. although i would like to see this card working before i buy a new card, if its possible.

thanks in advance

---

### Post by sirebral on 2008-12-28
I dislike ndiswrapper.  Good Luck with it.

In the meantime, check out the driver manufacturers site.  They might have a linux port for the device you are using.  It is Marvell Semiconductor

[http://www.marvell.com](http://www.marvell.com)

EDIT:  It was some Galileo thing: [http://www.yournewdriver.com/NETGEAR_WG311v3_802_11g_Wireless_PCI_Adapter_5903.htm](http://www.yournewdriver.com/NETGEAR_WG311v3_802_11g_Wireless_PCI_Adapter_5903.htm)

---

### Post by Clean1414 on 2008-12-28
i still need help, can anyone else or even the previous poster add anything to help me?

---

### Post by Lostin60's on 2008-12-28
Have you made sure you have the correct .sys file in the folder with your .inf file ?  If not, that could be your problem

---

### Post by sirebral on 2008-12-28
Well, here is another lead: [http://www.linuxforums.org/forum/wireless-internet/114655-wifi-driver-problem-netgear.html](http://www.linuxforums.org/forum/wireless-internet/114655-wifi-driver-problem-netgear.html)

That link provides access to a guide on setting up NDISWrapper.  One of the posters also mentions there is possibly a driver for your card written by the Red Hat team for OLPC.  You can find the info on that here: [http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#Libertas](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#Libertas)

If you still need help just ask.

---

### Post by melojo on 2008-12-28
Are you using a driver for Vista, if so try getting one for Win XP or 98.

---

### Post by Clean1414 on 2008-12-28
i was able to install the driver successfully but the card does not automaticly detect any wireless networks when my windows vista pc does, what do i need to do to get it to detect my wireless networks?

---

### Post by kevdog on 2008-12-28
I need some more background information.  Can you post the following:

lshw -C network
lspci -nnm

---

### Post by Clean1414 on 2008-12-28
> **kevdog said:**
> I need some more background information.  Can you post the following:

lshw -C network
lspci -nnm

user@Eubuntu:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:5b:92:e4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 76:e2:ff:0d:ae:cf
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
user@Eubuntu:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "ATI Technologies Inc [1002]" "RS480 Host Bridge [5950]" "Micro-Star International Co., Ltd. [1462]" "Device [7145]"
00:01.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a3f]" "" ""
00:11.0 "IDE interface [0101]" "ATI Technologies Inc [1002]" "IXP SB400 Serial ATA Controller [437a]" -p8f "Micro-Star International Co., Ltd. [1462]" "Device [7141]"
00:12.0 "IDE interface [0101]" "ATI Technologies Inc [1002]" "IXP SB400 Serial ATA Controller [4379]" -p8f "Micro-Star International Co., Ltd. [1462]" "Device [7141]"
00:13.0 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4374]" -p10 "Micro-Star International Co., Ltd. [1462]" "Device [7145]"
00:13.1 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB Host Controller [4375]" -p10 "Micro-Star International Co., Ltd. [1462]" "Device [7145]"
00:13.2 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "IXP SB400 USB2 Host Controller [4373]" -p20 "Micro-Star International Co., Ltd. [1462]" "Device [7145]"
00:14.0 "SMBus [0c05]" "ATI Technologies Inc [1002]" "IXP SB400 SMBus Controller [4372]" -r10 "Micro-Star International Co., Ltd. [1462]" "Device [7145]"
00:14.1 "IDE interface [0101]" "ATI Technologies Inc [1002]" "IXP SB400 IDE Controller [4376]" -p8a "Micro-Star International Co., Ltd. [1462]" "Device [7145]"
00:14.3 "ISA bridge [0601]" "ATI Technologies Inc [1002]" "IXP SB400 PCI-ISA Bridge [4377]" "Micro-Star International Co., Ltd. [1462]" "Device [7145]"
00:14.4 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "IXP SB400 PCI-PCI Bridge [4371]" -p01 "" ""
00:14.5 "Multimedia audio controller [0401]" "ATI Technologies Inc [1002]" "IXP SB400 AC'97 Audio Controller [4370]" -r01 "Micro-Star International Co., Ltd. [1462]" "Device [b000]"
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
01:05.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "RS480 [Radeon Xpress 200G Series] [5954]" "Micro-Star International Co., Ltd. [1462]" "Device [7141]"
02:01.0 "Ethernet controller [0200]" "Marvell Technology Group Ltd. [11ab]" "88w8335 [Libertas] 802.11b/g Wireless [1faa]" -r03 "Netgear [1385]" "Device [6b00]"
02:02.0 "Communication controller [0780]" "Conexant Systems, Inc. [14f1]" "HSF 56k Data/Fax Modem [2f20]" "Conexant Systems, Inc. [14f1]" "Device [2000]"
02:03.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL-8139/8139C/8139C+ [8139]" -r10 "Micro-Star International Co., Ltd. [1462]" "Device [145c]"
02:04.0 "FireWire (IEEE 1394) [0c00]" "VIA Technologies, Inc. [1106]" "VT6306 Fire II IEEE 1394 OHCI Link Layer Controller [3044]" -r80 -p10 "Micro-Star International Co., Ltd. [1462]" "Device [145d]"

---

### Post by kevdog on 2008-12-28
Ive only seen people describe using ndiswrapper with that card.  Do you possess a 64 bit windows driver with the card?

---

### Post by sirebral on 2008-12-28
Try enabling Wireless networking?  It says your network is disabled.

---

### Post by kevdog on 2008-12-28
No it states: 

*-network:0 UNCLAIMED 

Meaning that a correct driver has not claimed the device.  Hence you need to find the correct driver.

---

### Post by Clean1414 on 2008-12-29
> **kevdog said:**
> Ive only seen people describe using ndiswrapper with that card.  Do you possess a 64 bit windows driver with the card?

im almost 100% sure that it is a windows xp 64bit driver that i used and i did use ndiswrapper to install it but for some reason the card isnt picking up any wireless networks

---

### Post by Clean1414 on 2008-12-29
> **sirebral said:**
> Try enabling Wireless networking?  It says your network is disabled.

im pretty new to ubuntu, how do i enable it?

---

### Post by kevdog on 2008-12-29
Have you seen this post or blog:

[http://moosy.blogspot.com/2007/01/netgear-wg311v3.html](http://moosy.blogspot.com/2007/01/netgear-wg311v3.html)

Also can you list

ndiswrapper -l

Also try the following:
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

Then type dmesg and post only the relevant parts related to the ndiswrapper module insertion.  This is the system error log and will give you some clues.

Dont worry about enabling the device.  Without the correct driver it can not be enabled.

---

### Post by sirebral on 2008-12-29
Well, if you see the bars right click and make sure Enable Wireless is checked.

---

