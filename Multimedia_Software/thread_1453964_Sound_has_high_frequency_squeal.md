---
title: "Sound has high frequency squeal"
date: 2010-04-14
forum: Multimedia Software
---

### Post by 1clue on 2010-04-14
Hi,

Running Ubuntu 9.10 Karmic 64-bit.

Recently my previously functional sound has become unusable.  It still technically works, but there is an edge-of-hearing squeal that I can barely hear, but it HURTS when I play any sound, whether from a video site like YouTube or from any other "music" signal.  It even is there when there is no sound playing.

$ lspci
00:00.0 Host bridge: Intel Corporation X58 I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 12)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 12)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 12)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04)
02:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1)
04:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)
04:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)
05:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by uhappo on 2010-04-18
Sorry, I have no idea about your problem, but I have another question:

Is your TV-card working? You have a HP-desktop? I've got the exact TV-card and I'm trying to find a way to make it work, it's not working atm, apparently no drivers etc

---

### Post by lidex on 2010-04-18
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by 1clue on 2010-04-20
Never got the TV card to work, but I haven't really had time.  Actually, the squeal started happening about the same time I installed it, so I took it out just in case.  The squeal still happens.

FWIW, this squeal is similar to if my ears were ringing, only MUCH louder and a higher frequency.

$ uname -a
Linux thor 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux


$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech G35 Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.


$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC1200


Thanks.

---

### Post by lidex on 2010-04-20
I would suggest going here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
and following the directions for installing the alsa-backports.

---

### Post by 1clue on 2010-04-20
Thanks.  I'll give it a try.

---

### Post by 1clue on 2010-04-20
I tried that, and the squeal is still there.

$ dmesg | grep -i hda
[    9.978257] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.978302] HDA Intel 0000:00:1b.0: irq 56 for MSI/MSI-X
[    9.978323] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.207033] hda_codec: ALC1200: BIOS auto-probing.
[   10.208445] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8

Thanks.

---

### Post by renkinjutsu on 2010-04-20
I remember reading somewhere that the kernel timer is what causes it. Some people reported problems when their kernel timers are set to 1000Hz and that it's fine when set to 100Hz or dyntick (no_hz), and that is because most hardware is only tested on Windows, which has a kernel interrupt timer of 100Hz.. that's my understanding, and the whining noise comes from the high frequency timer... I don't know if that's your case though. Did this start happening after booting into a new kernel?

---

### Post by 1clue on 2010-04-20
I really can't say.

I rebooted, because I had put the TV card in.  So there might have been a kernel waiting for a reboot, but I don't remember.  I don't always reboot when the kernel upgrades come in, if I'm busy.

Is there an option to change the kernel timer frequency without recompiling the kernel?

---

### Post by 1clue on 2010-04-20
Or better yet, is there a relatively recent sound card that's good and has pretty much universal support?

---

