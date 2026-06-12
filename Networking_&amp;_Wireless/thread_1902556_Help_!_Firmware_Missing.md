---
title: "Help ! Firmware Missing"
date: 2011-12-31
forum: Networking &amp; Wireless
---

### Post by NetworkBoy on 2011-12-31
Hi, I recently installed Ubuntu into an old machine with Vista (wasn't quite working anymore). However, there is no internet connection. Under Network-Wireless, it says firmware missing. Under Additional Drivers it says downloading package indexes failed.
 
Heres my lspci -nn:
 
```
justin@justin-Aspire-X3600:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566DC-2 Gigabit Network Connection [8086:294c] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller [8086:2912] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller [8086:2922] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 2400 XT [1002:94c8]
01:00.1 Audio device [0403]: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO] [1002:aa10]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
04:06.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
04:07.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
04:07.1 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] [14f1:8801] (rev 05)
04:07.2 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] [14f1:8802] (rev 05)
justin@justin-Aspire-X3600:~$ 
```
 
I'm a total newbie to Ubuntu. Please help me! Thanks in advance!

---

### Post by praseodym on 2011-12-31
Hi,

missing firmware attached. Save it in your /home directory and unpack it to the right place via:

```
sudo tar xvf ~/Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
You can c/p this line

---

### Post by NetworkBoy on 2011-12-31
Thanks for the fast response and concise instructions! Worked very well!
Happy new year! Cheers!:KS

---

