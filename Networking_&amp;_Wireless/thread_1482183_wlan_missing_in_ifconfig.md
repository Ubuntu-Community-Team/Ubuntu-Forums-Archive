---
title: "wlan missing in ifconfig"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by abhinav.p on 2010-05-13
hi all i got my hands on a new lap top and was trying to connect it to the available wi fi network. after much work i found that the ifconfig shows no wlan and it only shows eth0 and lo. does this conclusively prove that wi fi card is not present in my lap top? the manual says it is optional but i want to make sure if it is there or not...

---

### Post by chili555 on 2010-05-13
> does this conclusively prove that wi fi card is not present in my lap top? the manual says it is optional but i want to make sure if it is there or not...No. It probably conclusively proves that no driver has attached and then created an interface. You can probably find it in a terminal command:```
lspci -nn
```One of the entries will probably look something like this:> 03:00.0 Network controller [0280]: Intel Corporation PRO/[COLOR="Red"]Wireless[/COLOR] 3945ABG [Golan] Network Connection [8086:4227] (rev 02)Post it here and we'll help get you going.

---

### Post by abhinav.p on 2010-05-14
thanks heres the output for lspci -nn in terminal


joel@joel-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 671MX [1039:0671]
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) [1039:0003]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] [1039:0968] (rev 01)
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev 01)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
00:05.0 IDE interface [0101]: Silicon Integrated Systems [SiS] SATA Controller / IDE mode [1039:1183] (rev 03)
00:0f.0 Audio device [0403]: Silicon Integrated Systems [SiS] Azalia Audio Controller [1039:7502]
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)

---

### Post by chili555 on 2010-05-14
I see nothing there that is wireless. Very rarely, an internal card is attached to an internal USB bus. I have never heard of it in a laptop but I see something new every day. Please detach any USB devices and run:```
lsusb
```If there is nothing attached, it should read:> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubIf you see something else, post it here and we'll help you. It's beginning to look like there is no wireless device installed.

---

### Post by Iowan on 2010-05-14
I doubt it'll show anything new, but **sudo lshw -C network** *should* provide details about your networking hardware.

---

### Post by knowNothing23 on 2012-01-19
My laptop has the same problems. I had run lsusb and shows almost the exact output posted earlier, but mine has a "Bus 006" too. 

My internet wireless capabilities are enabled once I start Ubuntu, but after sometime or mainly when I use Skype, my wireless becomes inactive and the wireless option does not figure on the internet icon.
Could you help me further? 

Thank you.

---

### Post by knowNothing23 on 2012-01-30
Can anyone help? I have given hours to solve this problem and I still can't.

Thank you.

---

### Post by chili555 on 2012-01-30
> **knowNothing23 said:**
> Can anyone help? I have given hours to solve this problem and I still can't.

Thank you.Please run and post:```
lsusb
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

