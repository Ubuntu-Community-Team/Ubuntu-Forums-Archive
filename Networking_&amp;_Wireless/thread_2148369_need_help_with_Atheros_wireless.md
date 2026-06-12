---
title: "need help with Atheros wireless"
date: 2013-05-22
forum: Networking &amp; Wireless
---

### Post by openation1 on 2013-05-22
hello everyone......... I have an issue with my laptop. its an inspiron b120 the wifi doesn't work because it doesn't have the right driver.. i dont know how to make it work. please help me I appreciate it

---

### Post by squakie on 2013-05-22
Post back the output of lspci so we can which of the Broadcom chip sets it is as that will make a difference as to what we suggest.

In the mean time, if you can temporarily hardwire your PC to the router you can try additional drivers to see if it finds/recommends anything.

---

### Post by alan9800 on 2013-05-22
you might try to solve your trouble by following these instructions:
**STA drivers**:```
cd /cdrom/pool/main/d/dkms
sudo dpkg -i dkms*
cd /cdrom/pool/main/p/patch
sudo dpkg -i patch*
cd /cdrom/pool/main/f/fakeroot
sudo dpkg -i fakeroot*
cd /cdrom/pool/restricted/b/bcmwl
sudo dpkg -i bcmwl-kernel-source*
```
[HR][/HR]**b43/b43 legacy**:```
cd /cdrom/pool/main/b/b43-fwcutter/
sudo dpkg -i b43-fwcutter*
```and then click on this link: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

---

### Post by wildmanne39 on 2013-05-22
*Thread moved to **Networking & Wireless**.*

---

### Post by openation1 on 2013-05-24
hi everyone, I have an issue with my laptop its a compaq presario cq56. I install 12.04 and it doesnt wanna get the wifi............. what can I do? please help me.... I would appreciated thank you

---

### Post by lethall1 on 2013-05-24
```
sudo lspci
```
paste here please

---

### Post by openation1 on 2013-05-25
hi everyone, I just install the 12.04 in my laptop but the wifi doesnt work please help me.... this is what it says...
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by openation1 on 2013-05-25
hello, i install 12.04 version in my laptop the wifi doesnt work at all please help .... i would appreciated... this is what it says.....
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by carl4926 on 2013-05-25
Your device is not broadcom
```
[COLOR=#000000]02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)[/COLOR]
```

I'd prefer to see
```
lspci -nnk
```Just the relevant part will do

---

### Post by openation1 on 2013-05-25
this is what it comes on...
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
    Subsystem: Hewlett-Packard Company Device [103c:1604]
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:3040]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1604]
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by QIII on 2013-05-25
Threads merged.

Please do not make duplicate posts.

Thanks.

---

### Post by carl4926 on 2013-05-25
Thank you for your PM, but it's better to keep info here
Your device has a driver
```
[COLOR=#000000]02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)[/COLOR]
[COLOR=#000000]Subsystem: Hewlett-Packard Company Device [103c:3040][/COLOR]
[COLOR=#000000]Kernel [/COLOR]**[COLOR=#800000]driver in use: ath9k[/COLOR]**[COLOR=#000000][/COLOR]
[COLOR=#000000]Kernel modules: ath9k[/COLOR]
```

Not one I'm familiar with, except it can be buggy.
compat-wireless might help, but can I point you to a comment by one of the devs
[https://forums.opensuse.org/english/get-technical-help-here/wireless/487148-new-name-compat-wireless.html](https://forums.opensuse.org/english/get-technical-help-here/wireless/487148-new-name-compat-wireless.html)

---

### Post by sanderj on 2013-05-25
> **carl4926 said:**
> Thank you for your PM, but it's better to keep info here
Your device has a driver
```
[COLOR=#000000]02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)[/COLOR]
[COLOR=#000000]Subsystem: Hewlett-Packard Company Device [103c:3040][/COLOR]
[COLOR=#000000]Kernel [/COLOR]**[COLOR=#800000]driver in use: ath9k[/COLOR]**[COLOR=#000000][/COLOR]
[COLOR=#000000]Kernel modules: ath9k[/COLOR]
```

Not one I'm familiar with, except it can be buggy.


Buggy? No problems for me: works out of the box:


```
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e025]
	Kernel driver in use: ath9k
```

IMHO the OP should what he/she experiences, and what help is needed.

---

### Post by coffeecat on 2013-05-25
@openation1, I have merged two earlier threads on the same subject to this. Please do not open multiple threads on the same subject. When someone suggests you post terminal output, please do so in the original thread - do not start a new thread.

**EDIT**: since lspci shows that you do not have Broadcom wifi, I have renamed the thread for you.

---

