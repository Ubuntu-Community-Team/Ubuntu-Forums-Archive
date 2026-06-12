---
title: "Installing Wireless Driver without Internet Access"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by Craven1203 on 2012-01-05
I'm using an old Dell Latitude Laptop with Ubuntu 11.10. I have a Netgear Wireless PC Card WG511 (v1 I believe) that I used with it prior to installing Ubuntu. Without purchasing a new cardbus I don't have a way to get online with the laptop directly so I haven't been able to follow the instructions I found with similar cases to get this card to work. Is it possible to download the driver on another computer and transfer it over? Will the windows driver work for it? This is my first time with Ubuntu so I apologize if this is a stupid question.

---

### Post by drpjkurian on 2012-01-05
Hi you can use Ndiswrapper. It is a Linux module which allows Ubuntu to use the Windows driver for wireless cards (in most cases)

---

### Post by Craven1203 on 2012-01-06
> **drpjkurian said:**
> Hi you can use Ndiswrapper. It is a Linux module which allows Ubuntu to use the Windows driver for wireless cards (in most cases)

Where do I get Ndiswrapper? or does it come with Ubuntu?

Also are there any directions for using it floating about? Do I just get the driver exe file for the wireless card and ndiswrapper (if not built in) and stick them on a usb and move them over to the ubuntu laptop then run ndiswrapper (how etc).. 

Sorry again for the trouble.

---

### Post by drpjkurian on 2012-01-07
Try this thread [http://ubuntuforums.org/showthread.php?t=1770222](http://ubuntuforums.org/showthread.php?t=1770222)

---

### Post by carl4926 on 2012-01-07
Actually it would be better if we see exactly the device details. If you open a terminal, post the result of

```
lspci -nnk
```

You probably don't need ndiswrapper. That option is really a last resort

---

### Post by Craven1203 on 2012-01-07
I managed to get internet by using my phone as a modem via USB which has made updating a bit easier. Still working on getting the wireless driver as apparently I need the inf file and I can't figure out how to get it.

Here is what you requested, thanks for the help

j@j-Latitude-CPx-H500GT:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
    Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
    Kernel modules: shpchp
00:03.0 CardBus bridge [0607]: Texas Instruments PCI1225 [104c:ac1c] (rev 01)
    Subsystem: Dell Device [1028:00aa]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
00:03.1 CardBus bridge [0607]: Texas Instruments PCI1225 [104c:ac1c] (rev 01)
    Subsystem: Dell Device [1028:00aa]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
    Kernel driver in use: ata_piix
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
    Kernel driver in use: uhci_hcd
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 02)
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4
00:08.0 Multimedia audio controller [0401]: ESS Technology ES1978 Maestro 2E [125d:1978] (rev 10)
    Subsystem: Dell Device [1028:00aa]
    Kernel driver in use: ES1968 (ESS Maestro)
    Kernel modules: snd-es1968
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility P/M AGP 2x [1002:4c4d] (rev 64)
    Subsystem: Dell Latitude CPt [1028:00aa]
    Kernel modules: atyfb
06:00.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)
    Subsystem: Netgear WG511 v2/v3 54 Mbps Wireless PC Card [1385:4800]
    Kernel modules: p54pci, prism54
j@j-Latitude-CPx-H500GT:~$ ^C
j@j-Latitude-CPx-H500GT:~$

---

### Post by d3v1150m471c on 2012-01-07
> **Craven1203 said:**
> I'm using an old Dell Latitude Laptop
[http://en.wikipedia.org/wiki/Category_5_cable](http://en.wikipedia.org/wiki/Category_5_cable)

---

### Post by Craven1203 on 2012-01-08
> **d3v1150m471c said:**
> [http://en.wikipedia.org/wiki/Category_5_cable](http://en.wikipedia.org/wiki/Category_5_cable)

Funny, it doesn't have that option built in. I can buy a cardbus for it, but it'd likely require a driver too.

---

### Post by carl4926 on 2012-01-08
```
06:00.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism  GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)
    Subsystem: Netgear WG511 v2/v3 54 Mbps Wireless PC Card [1385:4800]
    Kernel modules: p54pci, prism54
```
That's the device

It's not one I'm familiar with. But it appears to have modules loaded.

You mention a .inf file. Does that mean you are looking at the ndiswrapper route?

> Locate the XP drivers on the install CD that came with the device or if  you don't have it, download them from the manufacturer's site. Copy the *whole contents*  of the directory containing the XP .inf file to a directory anywhere in  your Ubuntu filesystem, e.g in the directory "ndiswrapper" located at  /path_to/ndiswrapper. For illustration, suppose the .inf is abcde.inf,  now located at /path_to/ndiswrapper/abcde.inf. Open a console and first  enter su to get rootly powers. Then enter the command ndiswrapper -i /path_to/ndiswrapper/abcde.inf. 

But I'm not sure I'd go there.

And as for ethernet
> Funny, it doesn't have that option built in. I can buy a cardbus for it, but it'd likely require a driver too. 	Would probably just work. Especially if you were selective.

---

### Post by d3v1150m471c on 2012-01-08
> **Craven1203 said:**
> Funny, it doesn't have that option built in. I can buy a cardbus for it, but it'd likely require a driver too.

LOL seriously? dell is just brilliant. btw,
```

lspci | grep -i network

```

probably a good way to start your driver search

---

### Post by Craven1203 on 2012-01-21
Intersil Corporation ISL3980 PrismGT/Prism Duette/ ISL 3886 Prism Javelin/Prism Xbow rev01

I googled that and found stuff for debian, but not sure that helps me much.. the search continues

---

### Post by Craven1203 on 2012-01-21
Using the information I found here: [http://ubuntuforums.org/showthread.php?t=1603413](http://ubuntuforums.org/showthread.php?t=1603413)

I managed to get it working :D

I'm a happy camper now

---

