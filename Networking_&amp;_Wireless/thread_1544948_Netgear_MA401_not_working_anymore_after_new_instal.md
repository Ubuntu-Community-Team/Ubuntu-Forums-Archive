---
title: "Netgear MA401 not working anymore after new install"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by mtausig on 2010-08-03
Hello!

I just reinstalled Lubuntu Lucid on my old Notebook (Dell LAtitude L400) which has a Netgear MA401 PCMCIA Wireless card. The card always used to work on this machine (I think I had Hardy installed previously), but not anymore in Lucid.

The cardbus controller is recogniced, but the card is not used:
```

steffi@shed:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
00:10.0 Communication controller: Agere Systems WinModem 56k (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```

```

steffi@shed:~$ lspcmcia 
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:0a.0)
steffi@shed:~$ pccardctl ident
Socket 0:
  no product info available

```

The syslog is not very informing either, upon removing and reinstalling the card, I just get
```

[ 2450.464237] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[ 2452.808089] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0

```

```
steffi@shed:~$ dmesg |grep -i cardbus
[    0.823396] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[   28.003816] yenta_cardbus 0000:00:0a.0: CardBus bridge found [1028:00dc]
[   28.003874] yenta_cardbus 0000:00:0a.0: Enabling burst memory read transactions
[   28.003893] yenta_cardbus 0000:00:0a.0: Using CSCINT to route CSC interrupts to PCI
[   28.003906] yenta_cardbus 0000:00:0a.0: Routing CardBus interrupts to PCI
[   28.003925] yenta_cardbus 0000:00:0a.0: TI: mfunc 0x01201272, devctl 0x64
[   28.236517] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0038, PCI irq 10
[   28.236535] yenta_cardbus 0000:00:0a.0: Socket status: 30000010

```

Manually loading the orinoco driver (which I remember the card used before) didn't help either.

Any ideas?

cheers
Mathias

---

### Post by mtausig on 2010-08-03
My bad. I forgot to reboot the laptop after installing linux-wlan-ng. Now it works.

---

