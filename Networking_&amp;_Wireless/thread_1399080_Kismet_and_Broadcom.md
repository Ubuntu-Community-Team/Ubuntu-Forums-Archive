---
title: "Kismet and Broadcom"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by lorakesz on 2010-02-05
Hi,
I have a problem with my network controller Broadcom 4353 and Kismet. I can't set "monitor mode".

```

lorakesz@lorakesz:~$ uname --all
Linux lorakesz 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

```I use **bcmwl-kernel-source**, **bcmwl-modaliases **packages.

```
lorakesz@lorakesz:~$ lspci -vv
08:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
    Subsystem: Dell Device 000e
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl

``````
lorakesz@lorakesz:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:219  Noise level:160
          Rx invalid nwid:0  invalid crypt:6  invalid misc:0

pan0      no wireless extensions.
```kismet.conf :

```
source=b43,eth1,Broadcom
``````

lorakesz@lorakesz:~$ sudo kismet
[sudo] password for lorakesz: 
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (Broadcom): Enabling monitor mode for b43 source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.
```I understand that Kismet couldn't set monitor mode, but I don't know why? Is this device driver fault?

Thanks,
lorakesz

---

### Post by mAsTERpEE on 2010-10-01
Try to use the kernel driver name as source.
Worked for me.

Example:

```
source=wl,eth1,Broadcom
```

or 

```
source=bcm4353,eth1,Broadcom

```
Also make sure your card is supported:
[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers]("http://www.aircrack-ng.org/doku.php?id=compatibility_drivers")

---

