---
title: "wlan and lan not working for evo n600c"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by aziond on 2011-12-03
I have just received an old compaq evo n600c with windows xp on it... and as soon as i got it i decided to upload ubuntu on it... before the install it said that i didnt have a internet connection... after the install it said i dont have any internet connections... so i ran the command **sudo lspci** and the only the results showed no network card or no wlan card. It  shows the *communication controller: Agere Systems LT WinModem (rev 02) but nothing else to be used for internet connection... Since I use Broadband that is pretty much not need... can anyone help? Thanks

---

### Post by praseodym on 2011-12-03
Hi,

can you show the terminal (CTRL+ALT+T) outputs of the commands:
```
uname -a
lspci -nnk
lsusb
lsmod
ifconfig -a
cat /etc/network/interfaces
iwconfig
rfkill list
route -n
sudo iwlist scan
```
Without any connection you can copy/paste the outputs into a textfile and upload ist. Which hardware is in use? Router/modem or single modem?

---

### Post by aziond on 2011-12-07
Im using a router/modem and theres no way i can give you all that info...but the **lspci --nnk** command shows...
  	 	 	 	 	 	   00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset Host Bridge [8086:3575] (rev 04)  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:0030]  
 	Kernel driver in use: agpgart-intel  
 00:01.0 PCI bridge [0604]: Intel Corporation 82830 830 Chipset AGP Bridge [8086:3576] (rev 04)  
 	Kernel modules: shpchp  
 00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:0030]  
 	Kernel driver in use: uhci_hcd  
 00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 02)  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:0030]  
 	Kernel driver in use: uhci_hcd  
 00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:0030]  
 	Kernel driver in use: uhci_hcd  
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)  
 	Kernel modules: shpchp  
 00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)  
 	Kernel modules: iTCO_wdt, intel-rng  
 00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:0030]  
 	Kernel driver in use: ata_piix  
 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:b111]  
 	Kernel driver in use: radeon  
 	Kernel modules: radeon, radeonfb  
 02:03.0 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:004e]  
 	Kernel driver in use: yenta_cardbus  
 	Kernel modules: yenta_socket  
 02:03.1 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:004e]  
 	Kernel driver in use: yenta_cardbus  
 	Kernel modules: yenta_socket  
 02:04.0 Communication controller [0780]: Agere Systems LT WinModem [11c1:0450] (rev 02)  
 	Subsystem: AMBIT Microsystem Corp. Evo N600c [1468:0450]  
 02:09.0 Multimedia audio controller [0401]: ESS Technology ES1988 Allegro-1 [125d:1988] (rev 12)  
 	Subsystem: Compaq Computer Corporation Device [0e11:0094]  
 	Kernel driver in use: Maestro3  
 	Kernel modules: snd-maestro3

---

### Post by praseodym on 2011-12-07
Try the other outputs. Copy/paste them into a textfile if possible. Not a single network card is shown. Try the commands with the "grep" filtering. 

| is AltGr+< as key combination

---

### Post by designerferro on 2011-12-08
I just remembered my old Compaq Evo N600c. Going to install Ubuntu 11.10 and i'll let you guys know.

---

### Post by praseodym on 2011-12-08
Or try to get the outputs with a Live-CD

---

### Post by aziond on 2011-12-09
I think that the main problem is that its not reading any of the equipped hardware... but this is the info you guys asked for...
  	 	 	 	 	 	   uname -a  
 Linux laptop-Evo-N600c 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux  
 laptop@laptop-Evo-N600c:~$ lspci -nnk  
 00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset Host Bridge [8086:3575] (rev 04)  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:0030]  
 	Kernel driver in use: agpgart-intel  
 00:01.0 PCI bridge [0604]: Intel Corporation 82830 830 Chipset AGP Bridge [8086:3576] (rev 04)  
 	Kernel modules: shpchp  
 00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:0030]  
 	Kernel driver in use: uhci_hcd  
 00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 02)  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:0030]  
 	Kernel driver in use: uhci_hcd  
 00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:0030]  
 	Kernel driver in use: uhci_hcd  
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)  
 	Kernel modules: shpchp  
 00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)  
 	Kernel modules: iTCO_wdt, intel-rng  
 00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:0030]  
 	Kernel driver in use: ata_piix  
 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:b111]  
 	Kernel driver in use: radeon  
 	Kernel modules: radeon, radeonfb  
 02:03.0 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:004e]  
 	Kernel driver in use: yenta_cardbus  
 	Kernel modules: yenta_socket  
 02:03.1 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]  
 	Subsystem: Compaq Computer Corporation Evo N600c [0e11:004e]  
 	Kernel driver in use: yenta_cardbus  
 	Kernel modules: yenta_socket  
 02:04.0 Communication controller [0780]: Agere Systems LT WinModem [11c1:0450] (rev 02)  
 	Subsystem: AMBIT Microsystem Corp. Evo N600c [1468:0450]  
 02:09.0 Multimedia audio controller [0401]: ESS Technology ES1988 Allegro-1 [125d:1988] (rev 12)  
 	Subsystem: Compaq Computer Corporation Device [0e11:0094]  
 	Kernel driver in use: Maestro3  
 	Kernel modules: snd-maestro3  
 laptop@laptop-Evo-N600c:~$ lsusb  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 laptop@laptop-Evo-N600c:~$ lsmod  
 Module                  Size  Used by  
 snd_maestro3           22973  2  
 snd_ac97_codec        105614  1 snd_maestro3  
 radeon                896428  3  
 ac97_bus               12642  1 snd_ac97_codec  
 snd_pcm                80244  2 snd_maestro3,snd_ac97_codec  
 snd_page_alloc         14073  1 snd_pcm 
 snd_seq_midi           13132  0  
 snd_rawmidi            25269  1 snd_seq_midi  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 ttm                    65184  1 radeon  
 binfmt_misc            13213  1  
 snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event  
 drm_kms_helper         40745  1 radeon  
 ppdev                  12849  0  
 joydev                 17322  0  
 snd_timer              28659  2 snd_pcm,snd_seq  
 drm                   180037  5 radeon,ttm,drm_kms_helper  
 pcmcia                 39671  0  
 snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq  
 yenta_socket           27230  0  
 snd                    55295  11 snd_maestro3,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 irda                  185091  0  
 pcmcia_rsrc            18292  1 yenta_socket  
 psmouse                73312  0  
 pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc  
 soundcore              12600  1 snd  
 parport_pc             32111  1  
 serio_raw              12990  0  
 i2c_algo_bit           13184  1 radeon  
 crc_ccitt              12595  1 irda  
 shpchp                 32345  0  
 lp                     13349  0  
 parport                36746  3 ppdev,parport_pc,lp  
 floppy                 60032  0  
 laptop@laptop-Evo-N600c:~$ ifconfig -a  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:108 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:108 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:8304 (8.3 KB)  TX bytes:8304 (8.3 KB)  
 

 laptop@laptop-Evo-N600c:~$ cat /etc/network/interfaces  
 auto lo  
 iface lo inet loopback  
 

 laptop@laptop-Evo-N600c:~$ iwconfig  
 lo        no wireless extensions.  
 

 laptop@laptop-Evo-N600c:~$ rfkill list  
 laptop@laptop-Evo-N600c:~$ route -n  
 Kernel IP routing table  
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface  
 laptop@laptop-Evo-N600c:~$ sudo iwlist scan  
 [sudo] password for laptop:  
 lo        Interface doesn't support scanning.

---

### Post by aziond on 2011-12-09
and designerferro... please let me know how that works out

---

### Post by praseodym on 2011-12-09
Looks like an old "Winmodem", see here

[http://martian.barrelsoutofbond.org/index.html](http://martian.barrelsoutofbond.org/index.html)

Dont know if it (still) works with new kernels

---

### Post by aziond on 2011-12-12
Well i thank you guys for all the help... I just gave up on getting the original hardware to work and went a bought a cheap usb wireless adapter.. plugged it in and everything works fine

---

