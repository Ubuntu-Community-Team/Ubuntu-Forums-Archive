---
title: "Wlan0 Hardblocked after exiting WPA_Supplicant / (Ubuntu 10.04 - Atheros AR5001X+)"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by christian2002 on 2013-07-10
Hello,

I am very new to Linux, but i want to learn it :-)

I have a problem with my wlan0 interface after exiting WPA_Supplicant with ^C. The Interface seems to be broken.....
The first connection with WPA_Supplicant works like a charm, i can surf  the web, access SSH by another PC and do all the Internet things :-)
After exiting WPA_Supplicant, i cant bring the interface UP again with ifconfig. I can't reconnect with WPA_Supplicant.

I do not use any GUI or the xwindow system. I'll do all on the Console.

Ifconfig gives following output :

```
SIOCSIFFLAGS: Unknown error 132
```


My WIFI Card : (lspci with some v's :-) )

```
00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
        Subsystem: Askey Computer Corp. Device 7005
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-
        Kernel driver in use: ath5k
        Kernel modules: ath5k

```

Driver Info :

```
filename:       /lib/modules/3.2.6/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     FA2500C2D3C1A3B6094E37C
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.2.6 SMP mod_unload CORE2 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           all_channels:Expose all channels the device can use. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)


```

KERNEL - Linux bt 3.2.6 #1 SMP Fri Feb 17 10:40:05 EST 2012 i686 GNU/Linux
WPA_SUPPLicant - wpa_supplicant v0.6.9

After rebooting, the Wifi works again, until i disconnect from my wifi.

Can anyone help me with this problem ?

greetings Chris


EDIT :

I found out, that my Card is Hardblocked in RF-Kill. This happens after i exit wpa_supplicant.
I tried to unload and reload the driver with modprobe - No Success
I tried to add "nohwcrypt" in ath5k.conf - No Success
I tried to block/unblock the Card in RF-Kill - No Success

I have no hardware Switch at my Laptop to enable / disable the Wifi.


Come on, please help me :-))

---

### Post by christian2002 on 2013-07-11
Now i got my AWUS036NH, a external USB Wifi adapter.

If I use this for connecting with wpa_supplicant, everything works fine. I can exit wpa_supplicant and this interface is not blocked in rfkill.
There is only a problem with the internal ath5k card.

---

### Post by praseodym on 2013-07-11
You know that 10.04 is outdated? Try to update the ath5k:
```

sudo apt-get install linux-backports-modules-wireless-lucid-generic build-essential linux-headers-generic dkms
```
Reboot.

You may want to try deactivating the hardware encryption of the driver:
```

echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

---

### Post by christian2002 on 2013-07-11
Thanks for the Tips, but it didn't work for me.

I installed everything and had an additional kernel in Grub.
But the Problem is on the 2.6 Kernel, too.

My main install has a 3.2.6 Kernel.

I noticed (before installing anything) that the problems sometimes not occour, after quitting WPA_Supplicant.
The Error is nearly not reproduceabel :-(

But i tried some research and pressed "FN+F2" serval times, after i quit wpa_supplicant and was not hard blocked.
But after pressing these Keys, the Card got hard blocked again.
The Problem does not only occur if i press the Keys, it occurs mostly after quitting wpa_supplicant, sometimes not, and very very often, if i press the keys.

But, if i boot and press the Keys, nothing bad happens and the card gets not hard blocked.......


Sorry for my baaaaaaad english ;-)

---

