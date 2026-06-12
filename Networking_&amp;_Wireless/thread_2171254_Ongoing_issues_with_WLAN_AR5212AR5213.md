---
title: "Ongoing issues with WLAN: AR5212/AR5213"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by Phallus^In^Wonderland on 2013-08-29
Hi,

For some time now I have a (mostly) working wireless connection.  But every now and then the network will hang for a brief period (sometimes only about 10 seconds, but anywhere up to 2 minutes!).  It is usable for the most part, but it is still annoying and would like to try and resolve this.

I thought that it may be bugs in older versions of Ubuntu, so I have upgraded to 13.04, but still have the same issue.  The adapter is a TP-Link WN651G.  Here is some other info:

```
lspci -vv

09:01.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Wireless Network Adapter (rev 01)
	Subsystem: Atheros Communications Inc. TRENDnet TEW-443PI Wireless PCI Adapter
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f9b00000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k

```

```
dmesg | grep -i ath

[   21.457240] ath5k 0000:09:01.0: registered as 'phy0'
[   22.061511] ath: EEPROM regdomain: 0x809c
[   22.061515] ath: EEPROM indicates we should expect a country code
[   22.061517] ath: doing EEPROM country->regdmn map search
[   22.061519] ath: country maps to regdmn code: 0x52
[   22.061521] ath: Country alpha2 being used: CN
[   22.061522] ath: Regpair used: 0x52
[   22.256381] ath5k: phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[  457.707055] ath5k: ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x00000000
```


The last line of dmesg I get repeated some times, but it does not come up everytime the wireless drops out, so not sure if it has anything to do with it or not.  I have no idea what it means.

I have already tried installing MadWifi to see if this works any better.  It doesn't, in fact I get no connectivity with the ath_pci driver.  It says it connects to the AP (albeit with a very poor signal) but you cannot transfer any data at all.

Any help at all would be appreciated.  Let me know if you need any other info.

TIA.

---

### Post by praseodym on 2013-09-01
Hi,

uninstall the madwifi driver and deactivate the hardware encryption of the Atheros driver:
```

echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

---

### Post by Phallus^In^Wonderland on 2013-09-02
If I do this, does this mean that I cannot use WEP/WPA encryption?  Or does it just do it in software?  If it is the former, this isn't acceptable, I can't have an open wireless network.  Thanks for your response.

---

### Post by praseodym on 2013-09-03
No, you can still use any encryption, incl. WPA2

---

### Post by Phallus^In^Wonderland on 2013-09-05
Well, so far so good!  I haven't noticed this issue in the last couple of days.  Thanks praseodym for your help!

---

