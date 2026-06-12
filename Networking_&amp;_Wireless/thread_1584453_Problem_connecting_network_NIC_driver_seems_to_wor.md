---
title: "Problem connecting network: NIC driver seems to work"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by garrapito on 2010-09-29
Hello,

I have a problem connecting to internet at my work. I installed Lubuntu 9.10, with 2.6 kernel, that already has the Broadcom tg3 driver for my the NIC I use, "Broadcom NetXtreme 57xx Gigabit Controller" (I checked the vendor). The problem is:
[LIST]
[*]Network tools can not access to the internet, somehow they do not see my LAN wire (wich is a standard wire).
[*]The LAN cable does not seem to be broken, works in windows, and I have the same problem with other cables.
[*]The tg3 driver seems to be working and activated. I include the information I obtained using dmesg and lspci.
[/LIST]


[INDENT]garrapito@snorlax:~$ lspci -vvv

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
	Subsystem: Dell Device 0175
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at dcff0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

garrapito@snorlax:~$ dmesg | grep tg3

[    1.532485] tg3.c:v3.102 (September 1, 2009)
[    1.532508] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.532521] tg3 0000:02:00.0: setting latency timer to 64
[   11.667204] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   11.667209] tg3: eth0: Flow control is on for TX and on for RX.[/INDENT]


So, basically, I have no clue about where the problem is. Any ideas? Thanks in advance.

---

### Post by cavalier911 on 2010-09-29
The linux driver for this hardware has a track record of not working. 

Open terminal.

Verify interface is installed:

Post results from:
```
sudo ifconfig -a
``````
sudo lshw -C Network
```Where in connection process is failure ?

Kill NetworkManager:
```
sudo service network-manager stop
```Start NetworkManager in debug mode:
```
sudo NetworkManager --no-daemon
```

---

