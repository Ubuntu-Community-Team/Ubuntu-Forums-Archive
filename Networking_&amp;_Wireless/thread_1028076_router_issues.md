---
title: "router issues"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by smurfgod on 2009-01-02
i have a wireless router..netgear...and my system dosent recognize it.does anyone know how to fix it???

smurf   :confused:

---

### Post by superprash2003 on 2009-01-02
post output of **iwlist scanning** from terminal .. have you configured wifi correctly in netgear?? is some other laptop able to connect?

---

### Post by Kevbert on 2009-01-02
What's your wireless card ? It's possible that you need to install some firmware drivers. Please enter the following commands in Applications-Accessories-terminal and post the resulting output.
```
lspci
iwconfig
```
You can copy the output by highlighting it with the mouse and press Ctrl-Shift-C to copy and Ctrl-V to paste it here.

---

### Post by smurfgod on 2009-01-02
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] PCI Bridge
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
and thats what it says....

---

### Post by Kevbert on 2009-01-03
The wireless hasn't been detected by Ubuntu according to your last post.
Is the wireless adapter USB ?  If so you need to try this in terminal instead:
```
lsusb
```
Another thing you could try is go to System-Administration-Software Sources and make sure that Proprietary drivers for devices is ticked under the Ubuntu Software tab and Unsupported updates is ticked under the Updates tab. Reload the updates list when prompted. Now go to System-Administration-Hardware Drivers and see if your wireless adapter is shown there and if so enable the driver.
Am I correct in assuming the PC is quite old (using the MX440 video) ?
What is the PC make, model. If it's a laptop, do you have a front panel switch to turn on wireless ? If so, try pressing it once and see if it's detected via
```
lspci
```

---

### Post by smurfgod on 2009-01-03
Bus 005 Device 012: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 016: ID 03f0:4b11 Hewlett-Packard Officejet 6200
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
this is what i got when i went to terminal and typed lsusb.

00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] PCI Bridge
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
this is what i got when i typed lspci from terminal.
  i have a netgear wireless n router wnr2000.can i hook up to someone elses wireless network.i know when i had my lappy i was.there are so many around me in a town this small.i have my cabel modem and my vonage thingy hooked up.

and my comp is a desktop frankenstein.me and my dad put it together from like 3 different ones.

---

### Post by smurfgod on 2009-01-03
Another thing you could try is go to System-Administration-Software Sources and make sure that Proprietary drivers for devices is ticked under the Ubuntu Software tab and Unsupported updates is ticked under the Updates tab. Reload the updates list when prompted. Now go to System-Administration-Hardware Drivers and see if your wireless adapter is shown there and if so enable the driver.

i did all that and the router didnt come up.  :confused:

---

### Post by Kevbert on 2009-01-04
Ubuntu is not seeing any wireless adapter in your PC.  Are you sure it has either wireless built in on the motherboard? What is the motherboard make/model ? If you have a separate wireless card, check that the card is properly plugged into the motherboard.

---

### Post by smurfgod on 2009-01-04
Bus 005 Device 004: ID 05dc:a720 Lexar Media, Inc. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 03f0:4b11 Hewlett-Packard Officejet 6200
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


terminal<----lsusb

---

