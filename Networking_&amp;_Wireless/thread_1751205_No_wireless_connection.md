---
title: "No wireless connection"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by jazco001 on 2011-05-06
Hello, I am new to Ubuntu and I am having problems connecting to the Internet wirelessly. I recently installed Ubuntu into my HP laptop and ever since I did my laptop does not get any wireless networks. Thank you for your help, Jorge.

---

### Post by josephmills on 2011-05-06
> **jazco001 said:**
> Hello, I am new to Ubuntu and I am having problems connecting to the Internet wirelessly. I recently installed Ubuntu into my HP laptop and ever since I did my laptop does not get any wireless networks. Thank you for your help, Jorge.

hi there Jorge and welcome to ubuntuforums could you please open you terminal and type in 
```
lspci -nn 
```
then ```
rfkill list all 
```
and paste it all here thanks and once agian welcome to ubuntuforums if you have any questions just ask (a dumb question is none at all -MLKjr)

---

### Post by jazco001 on 2011-05-06
Thank you very much for your quick response, below is everything that came up from the terminal... 
Jorge.

jorge@jorgeLuis-Pavilion-ZV6100-PN494AV:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 10)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 01)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 01)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
03:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
03:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
03:04.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
03:04.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
03:04.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
03:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
jorge@jorgeLuis-Pavilion-ZV6100-PN494AV:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jorge@jorgeLuis-Pavilion-ZV6100-PN494AV:~$

---

### Post by josephmills on 2011-05-06
cool thanks could we now see a 
```
lsmod | grep b43 
```
and a 
```
dmesg | grep b43 
```
thanks again

---

### Post by jazco001 on 2011-05-06
Yes, I am finally connected to the Internet wirelessly. Thank you very much for your help and time, I really appreciate it. 
Regards, 
Jorge.

---

