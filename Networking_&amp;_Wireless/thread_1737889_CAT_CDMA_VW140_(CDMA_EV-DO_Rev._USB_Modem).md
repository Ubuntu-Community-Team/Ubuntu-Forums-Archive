---
title: "CAT CDMA VW140 (CDMA EV-DO Rev. USB Modem)"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by jitttue on 2011-04-24
Hello.

 I'm new to linux.
I just installed UBUNTU 10.10.. 
I Don't Know How to Install Driver For My Modem
[COLOR=Red]CAT CDMA VW140 (CDMA EV-DO Rev. USB Modem[/COLOR])
I Have Driver For My Modem and User Guide ..But I Can't
Any Advice ?:D
Thanks..

---

### Post by josephmills on 2011-04-24
lets take a look at your system press ctrl+alt+t then enter ```
lspci
``` then paste it here

---

### Post by jitttue on 2011-04-24
Dear .. Here Is It..



[FONT=&quot]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

momohein@momohein-P4M89-M7B:~$ ISPCI
ISPCI: command not found
momohein@momohein-P4M89-M7B:~$ 

 [/FONT]

---

### Post by josephmills on 2011-04-24
> **jitttue said:**
> Dear .. Here Is It..



[FONT=&quot]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

momohein@momohein-P4M89-M7B:~$ ISPCI
ISPCI: command not found
momohein@momohein-P4M89-M7B:~$ 

 [/FONT]

sorry about that I should have been more clear it is Lspci with no caps lspci l as in llama :D

---

### Post by jitttue on 2011-04-24
> **josephmills said:**
> sorry about that I should have been more clear it is Lspci with no caps lspci l as in llama :D

It's..:D..I Know Nothing About UBUNTU..
Anyway.. Thanks ..
Here Is It..


 [FONT=&quot]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

momohein@momohein-P4M89-M7B:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. P4M890 [S3 UniChrome Pro] (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
momohein@momohein-P4M89-M7B:~$ 


 [/FONT]

---

### Post by josephmills on 2011-04-24
could we now see the things that are in the usb ports ```
lsusb
```thanks

---

### Post by jitttue on 2011-04-24
> **josephmills said:**
> could we now see the things that are in the usb ports ```
lsusb
```thanks

Here We Are..
Sorry For Late.. I Using Duel Boot On One Computer...(Window 7 & Ubuntu )That Why.:p.. Thanks For Using Your Time..

 [FONT=&quot]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

momohein@momohein-P4M89-M7B:~$ lsusb
Bus 005 Device 002: ID 1fe7:0100 Vertex Wireless Co., Ltd. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04e8:342e Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
momohein@momohein-P4M89-M7B:~$ 

 [/FONT]

---

### Post by josephmills on 2011-04-24
how about a ```
rfkill list all 
```

---

### Post by jitttue on 2011-04-24
> **josephmills said:**
> how about a ```
rfkill list all 
```

This Time Nothing See..
```
  [FONT=&quot]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

momohein@momohein-P4M89-M7B:~$ rfkill list all
momohein@momohein-P4M89-M7B:~$ 

 [/FONT]
  
```

---

