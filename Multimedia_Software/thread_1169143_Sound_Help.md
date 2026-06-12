---
title: "Sound Help"
date: 2009-05-24
forum: Multimedia Software
---

### Post by Nbasil on 2009-05-24
hi everyone, 
im somewhat new with ubuntu so please bear with me

i have installed ubuntu 8.10 and recently upgraded to 9.04 and unfortunately my sound will not work, now I have tried every trick i could find and it still wont work. 

this is my lspci list
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:08.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
00:09.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0d.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0d.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0d.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GT] (rev a1)

can someone tell me if my sound card is compatable with ubuntu cause i think that is the only explination i have left

---

### Post by HousieMousie2 on 2009-05-24
My old Audigy was supported and worked well with Hardy Heron. I do not know if there are any issues with newer releases.

[ALSA Matrix - List of sound cards (by vendor) Creative Labs page]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs")

One of these will probably work for you: emu10k2,CA0151/P16V


You can use the following command to find out what is loading.

```
cat /proc/modules
```


This is useful for getting more information about how your card is seen.

```
cat /proc/asound/cards
```

```
aplay -L
```
^Works too, little different info, though.

The more info you can provide, the more likely that people with be able to help you the first time.

---

### Post by Nbasil on 2009-05-24
Thank you so much for replying so fast,
but how do i get these drivers i dont seem to see an option to download them.

---

### Post by HousieMousie2 on 2009-06-10
Sorry, I didn't check back with you until now...

I could be wrong, but I believe those drivers should all be packaged together with the latest release of ALSA.

You could try downloading and installing from here:

(I would say everything except the Firmware and PyALSA.)

[ALSA Download]("http://www.alsa-project.org/main/index.php/Download")

But that would not be my first choice...

Have you gone through any of the HOWTO's?

Like this one:

[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")

At the very least, it may give you something new to try.

---

### Post by Nbasil on 2009-06-25
hi there, thanks for the help so far but everything i do doesnt seem to work, a while back i was able to get sound working by simply pluging one of the wires for my speakers into my headphone jack, unfortunatly alittle while ago my computer crashed and i had to gut the whole thing, now i no longer have windows(something about not likeing extreme hardware shifts) and ubuntu is running perfectly except the fact that no sound comes out of the thing once i log in. it will make the few noises when im on the login screen and thats it. Also, i think i have all the drivers for the audigy soundblaster card that i have cause it is recognized by the computer its just not doing anything.

any suggestions?

here is my new lspci list if it helps
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
03:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
03:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

---

### Post by Nbasil on 2009-06-27
scratch that last one, ive gotten sound working by pluging my speakers into the speaker plugs in my motherboard and all sound setting set to OSS, but the firefox and vlc play videos but i get no sound from them. is there any way to fix this?

---

