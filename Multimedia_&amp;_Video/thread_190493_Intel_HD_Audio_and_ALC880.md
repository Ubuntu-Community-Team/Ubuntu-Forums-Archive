---
title: "Intel HD Audio and ALC880"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by Burkey on 2006-06-06
Hi, I have an Intel ICH7 based sound card coupled with the ALC880 chip.

The thing plays nice sound out the headphones and even turns on a nice red led out the digital port when I enable it.  My problem though is that the built-in speakers will not make a sound!

My computer is an LG P1 Express Dual laptop, lspci yields:
```

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:02:00.0 Ethernet controller: Agere Systems: Unknown device ed00 (rev 02)
0000:05:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:06:00.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:06:00.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:06:00.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:06:00.3 0805: Texas Instruments: Unknown device 803c

```

cat /proc/asound/cards
```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd8500000 irq 74

```

I tried to install Alsa 1.0.11 from the alsa-project web site, it seemed to go in but also seemed to not make a difference which makes me wonder if the .ko I built it actually in and running or if the Ubuntu kernels one is instead (how do I check that?)

---

### Post by Burkey on 2006-06-07
Hmm, no suggestions?

---

### Post by Burkey on 2006-06-12
Is anyone able to tell me how to check my Alsa DRIVER version?  I think 1.0.11 is instaled but am not sure.  If it is and it still will not work correctly, then perhaps it does not support the ALC880?  Seems some others are having problems with these too so it would be good if I can find a solution and post here.

---

### Post by dan4444 on 2006-06-12
I have the same exact sound card as you, and I have found my solution. - see thread at [http://www.ubuntuforums.org/showthread.php?t=195434](http://www.ubuntuforums.org/showthread.php?t=195434)

---

