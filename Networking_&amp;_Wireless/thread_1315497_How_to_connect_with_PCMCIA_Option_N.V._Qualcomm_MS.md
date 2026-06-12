---
title: "How to connect with PCMCIA Option N.V. Qualcomm MSM6275 ?"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by stando007 on 2009-11-05
Hi, I have this datcard from Orange Slovakia. I am currently not able to connect in Ubuntu 9.10. When I insert the card into PCMCIA dmesg says:
```

[15294.636060] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[15294.636106] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x0007ff]
[15294.675149] Initializing Nozomi driver 2.1d (build date: Oct 16 2009 14:21:24)
[15294.675200] nozomi 0000:03:00.0: Init, new card found
[15294.675213] nozomi 0000:03:00.0: enabling device (0000 -> 0002)
[15294.675227] nozomi 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[15294.675235] nozomi 0000:03:00.0: Card type is: 2048
[15294.966171] nozomi 0000:03:00.0: Version of card: 3
[15294.966530] nozomi 0000:03:00.0: Initialization OK!
[15295.570131] nozomi 0000:03:00.0: Device READY!
```

But nothing happens after that. No new connection is not present in Network Manager. If I add new broadband connection in Network Manager, I do not have possibility to choose it for connecting.

Anybody can help me?

---

### Post by stando007 on 2009-11-08
No ideas?

---

### Post by TDewin on 2009-11-09
Having the same problem here. Going to try to get the latest networkmanager from dev [https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk) , [https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware) . No idea if it is going to help though

---

### Post by jarwadi on 2009-11-11
> **TDewin said:**
> Having the same problem here. Going to try to get the latest networkmanager from dev [https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk) , [https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware) . No idea if it is going to help though
i just updated my network manager by following the given link, but still can not connected. The network manager sometimes can recognize my modem after upgrade but failure to connect

---

### Post by robnunin on 2009-11-18
Same situation here, Option Card from Vodafone, discovered not each boot.
dmesg is the same.

I'm running filea Karmic release, updated 10 minutes ago.

NetworkManager is release 0.7.996

---

### Post by thesemey on 2009-11-18
Hi,

same issue here with Vodafone Option 3G+ EMEA "MSM6275" card - I cannot connect either.
I do not have the full solution, but a small part of it, whenever the network-manager applet does not show my broadband device:

sudo killall modem-manager

Do not bother, the network-manager will automatically restart this process - and voila, by magic your device shows up in nm_applet.

Seems to be an issue that multiple PCMCIA cards suffer with karmic, that all worked with former Ubuntu releases.

Several **PCMCIA cards** seem to be involved:
* Option Qualcom 3G+ EMEA MSM6275 card using *nozomi* kernel module
* Sierra pcmcia card using *usbserial* kernel module
* SonyEricsson PC300 cards

But the **USB** Huawei E620 USB Modem works with Karmic ... so it is not a general broadband issue.

What I constantly see is:
**pppd via network manager**: <WARN> pppd_timed_out(): Looks like pppd didn't initialize our dbus module
**pppd via wvdial**: LCP: timeout sending Config-Requests
**umtsmon**: complains about receive Sting: '(null)' after endlessly waiting for an UMTS card response

---

### Post by stando007 on 2009-12-09
I have updated network manager from daily ppa trunk - now when I insert PCMCIA card, I see broadbang connection in network manager applet, but still I am not able to connect:

**modem-manager: Got failure code 100: Unknown error**

```
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  Activation (noz2) starting connection 'Orange Default 1'
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  (noz2): device state change: 3 -> 4 (reason 0)
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  Activation (noz2) Stage 1 of 5 (Device Prepare) scheduled...
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  Activation (noz2) Stage 1 of 5 (Device Prepare) started...
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  (noz2): device state change: 4 -> 6 (reason 0)
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  Activation (noz2) Stage 1 of 5 (Device Prepare) complete.
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  Activation (noz2) Stage 1 of 5 (Device Prepare) scheduled...
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  Activation (noz2) Stage 1 of 5 (Device Prepare) started...
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  (noz2): device state change: 6 -> 4 (reason 0)
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  Activation (noz2) Stage 1 of 5 (Device Prepare) complete.
Dec  9 09:25:38 ygzo-laptop modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Dec  9 09:25:38 ygzo-laptop modem-manager: Got failure code 100: Unknown error
Dec  9 09:25:38 ygzo-laptop modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> disabled)
Dec  9 09:25:38 ygzo-laptop NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: Unknown error
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  (noz2): device state change: 4 -> 9 (reason 1)
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  Marking connection 'Orange Default 1' invalid.
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  Activation (noz2) failed.
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  (noz2): device state change: 9 -> 3 (reason 0)
Dec  9 09:25:38 ygzo-laptop NetworkManager: <info>  (noz2): deactivating device (reason: 0).
```

Any ideas?

---

