---
title: "Dell 1018: Unable to remove wireless hardware block"
date: 2012-01-15
forum: Networking &amp; Wireless
---

### Post by MusicalLoop on 2012-01-15
Hi, I'm having problems getting my wireless to work after pressing the hotkey to disable it I am unable to re-enable it. I've seen several posts on this forum and tried to follow them but I've still not able to remove the hardware block on my RealTek wireless card.

I've tried removing the dell_laptop kernel module:

```
andy@Mini-Loop:~$ sudo lsmod | grep dell
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
andy@Mini-Loop:~$ sudo rmmod -f dell_laptop 

andy@Mini-Loop:~$ sudo rfkill unblock all

andy@Mini-Loop:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

iwconfig:
```
andy@Mini-Loop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
usb0      no wireless extensions.

```

lspci -nn:
```
andy@Mini-Loop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
```



I tailed the /var/log/syslog and every time I press the hotkey (F2) to enable wireless I get the following error message:
```
Jan 15 21:11:04 Mini-Loop kernel: [ 6390.952911] keyboard: can't emulate rawmode for keycode 240
Jan 15 21:11:04 Mini-Loop kernel: [ 6390.952948] keyboard: can't emulate rawmode for keycode 240
```

Any help gratefully received.
Andy

---

### Post by MusicalLoop on 2012-01-22
The only way I was able to resolve this was to do a clean install of 11.04. I did try 11.10 but this didn't work.

---

