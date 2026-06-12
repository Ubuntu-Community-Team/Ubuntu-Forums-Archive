---
title: "Can anybody help get M-Audio Delta 66 working in 10.10 fresh install?"
date: 2012-03-20
forum: Multimedia Software
---

### Post by ingramproductions on 2012-03-20
I've looked around and others said it works out of box, but I can't get my Delta 66 working. Here is some info that might give you clues to why it's not working:

```
lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
01:01.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications L2 Fast Ethernet (rev a0)
04:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
04:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M66 [M Audio Delta 66], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I've disabled the on-board audio card in BIOS. Since aplay -l displays the M-Audio card, we at least know my system recognizes the card. What do I need to do to make it work?

Thanks

---

### Post by lykwydchykyn on 2012-03-20
In what way is it not working?

I have the Delta 44, I find that most desktop volume/mixer applets choke on it.  I've been using the envy 24 mixer with it, though, and it works great. 

Most likely your volumes are all turned down, and you need the mixer program to turn them up.

---

### Post by ingramproductions on 2012-03-20
I get no audio output. I've attached screenshots of the "Sound Preferences" menu and of the Envy24 Control Utility. On the "Patchbay/Router" tab of Envy24, I tried all the combinations for the outputs, and still no luck.

Not sure what I'm doing wrong here. I can provide anymore screenshots you think would be useful. I also tried all the combinations on the Sound Preferences menu.

Thanks

---

### Post by lykwydchykyn on 2012-03-21
Check your "analog volumes" tab in envy24.  Make sure all the DAC volumes are turned up.

---

### Post by ingramproductions on 2012-03-22
The "Analog Volume" tab has all the volumes turned up as well. (I forgot to add that screenshot with the rest of them).

Any other ideas?

---

### Post by lykwydchykyn on 2012-03-23
When you route sound to it, do any of the meters light up in envy?

Also, I noticed in the screenshots all your monitor busses are muted.  I assume you tried to unmute all these?

---

### Post by ingramproductions on 2012-04-06
> **lykwydchykyn said:**
> When you route sound to it, do any of the meters light up in envy?

Also, I noticed in the screenshots all your monitor busses are muted.  I assume you tried to unmute all these?

When you say route sound to it, I assume you mean on the Patchbay/Router tab.
No, none of the lights light up and I have unchecked all the mute buttons.

---

