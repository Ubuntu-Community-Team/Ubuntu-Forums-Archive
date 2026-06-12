---
title: "Lost all sound on Thinkpad T43 running Karmic9.10"
date: 2010-03-12
forum: Multimedia Software
---

### Post by airbuntu on 2010-03-12
Hi

I've been running 9.10 for a while now without any issues until recently when a watched a youtube clip that may have crashed pulseaudio. I've tried restarting/reinstalling pulseaudio but still no luck. I have also tried going through the Comprehensive Sound Guide but still have no sound. Quite frankly I don't even know what's wrong as everything was working fine before.

Can anyone suggest how to narrow in on the problem or a solution even?

I have checked:

1) Volume control: volume is up
2) Alsamixer: all channels unmuted
3) Pulse audio volume control: can see the volume meter increasing/deceasing when playing mp3s
4) Output of aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```5) Output of lspci -v

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
    Subsystem: IBM Device 0575
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: a8100000-a81fffff
    Prefetchable memory behind bridge: c0000000-c7ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: a8200000-a82fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: a8300000-a83fffff
    Prefetchable memory behind bridge: 00000000c8000000-00000000c80fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
    Subsystem: IBM Device 0565
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
    Subsystem: IBM Device 0565
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
    Subsystem: IBM Device 0565
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
    Subsystem: IBM Device 0565
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
    Subsystem: IBM Device 0566
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at a8000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=07, sec-latency=168
    I/O behind bridge: 00005000-00008fff
    Memory behind bridge: a8400000-b7ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d7ffffff
    Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
    Subsystem: IBM Device 0567
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 1c00 [size=256]
    I/O ports at 1880 [size=64]
    Memory at a8000800 (32-bit, non-prefetchable) [size=512]
    Memory at a8000400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
    Subsystem: IBM Device 0574
    Flags: medium devsel, IRQ 23
    I/O ports at 2400 [size=256]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0m

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
    Subsystem: IBM Device 0568
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
    Subsystem: IBM Device 056a
    Flags: bus master, 66MHz, medium devsel, latency 0
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 18c0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
    Subsystem: IBM Device 056b
    Flags: medium devsel, IRQ 11
    I/O ports at 18e0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
    Subsystem: IBM Device 056e
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at c0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 3000 [size=256]
    Memory at a8100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at a8120000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon, radeonfb

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
    Subsystem: IBM Device 0577
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at a8200000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

04:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
    Subsystem: IBM Device 056c
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at a8410000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=04, secondary=05, subordinate=06, sec-latency=176
    Memory window 0: d0000000-d3fff000 (prefetchable)
    Memory window 1: ac000000-affff000
    I/O window 0: 00005000-000050ff
    I/O window 1: 00005400-000054ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

04:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
    Subsystem: IBM Device 057e
    Flags: bus master, fast Back2Back, medium devsel, latency 168, IRQ 21
    Memory at a8400000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k
```6) Output of cat /etc/modules

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

snd-intel8x0
```7) Output of uname -r

```
2.6.31-20-generic
```

---

### Post by tgalati4 on 2010-03-12
Look for any strange behavior in:

dmesg | tail -50

If nothing strange and the following command doesn't work:

pulseaudio -k

Then you have to go to plan B.

Shut down the machine.  Remove the battery for 10 minutes.  Install the battery and reboot.

Play some music.

I have a T43p and I've never experienced any such behavior.

---

### Post by airbuntu on 2010-03-12
Thanks tgalati4. I have a heap of:

[ 4651.339320] ath5k phy0: noise floor calibration timeout (2437MHz)

from dmesg but I presume that would be more to do with a temporary disruption to my wireless signal than my soundcard...

Are there any other logs or anything of any sort where I can go hunting for sound error messages? Or specific pulseaudio or alsa settings that I should check?

---

### Post by Yellow Pasque on 2010-03-12
If you delete the hidden .pulse file/folder in you home dir, does it help?

---

### Post by airbuntu on 2010-03-13
yep, tried deleting .pulse and rebooting/shutting down several times... still the same...still no sound...

---

### Post by tgalati4 on 2010-03-13
If I understand correctly, the southbridge chip (ICH6) controls networking, usb, and sound dsp.  So let's check the interrupts:

cat /proc/interrupts

tgalati4@tpad-Gloria7 ~ $ uptime
 11:50:52 up 16 days, 19:53,  5 users,  load average: 0.33, 0.66, 0.81
tgalati4@tpad-Gloria7 ~ $ cat /proc/interrupts
           CPU0       
  0:   25331811   IO-APIC-edge      timer
  1:     133104   IO-APIC-edge      i8042
  4:          8   IO-APIC-edge    
  7:          0   IO-APIC-edge      parport0
  8:          1   IO-APIC-edge      rtc0
  9:   11901521   IO-APIC-fasteoi   acpi
 12:   26243448   IO-APIC-edge      i8042
 14:     405297   IO-APIC-edge      ata_piix
 15:       1435   IO-APIC-edge      ata_piix
 16:     398146   IO-APIC-fasteoi   uhci_hcd:usb2, yenta, radeon@pci:0000:01:00.0, eth0
 17:          1   IO-APIC-fasteoi   uhci_hcd:usb3
 18:       2786   IO-APIC-fasteoi   uhci_hcd:usb4
 19:       3314   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5
 21:    6281188   IO-APIC-fasteoi   ipw2200
 22:   13461457   IO-APIC-fasteoi   Intel ICH6
NMI:          0   Non-maskable interrupts
LOC:   23555878   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0

Do you have any USB devices connected?  Try turining the wireless off and leaving off then rebooting.  We need to isolate as many functions from the ICH6 chip as possible.  It's possible that the southbridge "went south".  Heat and flexing of the main board can cause failures.

Boot a live Karmic CD and see if sound works in any applications.

I'm suspecting hardware failure, because sound usually works well on thinkpads.  The fact that you were watching youtube--drives the southbridge pretty hard--both high networking and sound simultaneously.  I've seen such failures in desktop Intel southbridge chips (eMachines had problems) when streaming audio for long periods of time.  The southbridge chip heats up and fails.

---

### Post by airbuntu on 2010-03-14
my interrupt output is

```
will@w-ubuntu:~$ uptime
 10:34:45 up 51 min,  2 users,  load average: 0.00, 0.00, 0.07
will@w-ubuntu:~$ cat /proc/interrupts
           CPU0       
  0:      85397   IO-APIC-edge      timer
  1:       1852   IO-APIC-edge      i8042
  4:          2   IO-APIC-edge    
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          1   IO-APIC-edge      rtc0
  9:       9351   IO-APIC-fasteoi   acpi
 12:       4586   IO-APIC-edge      i8042
 14:      34094   IO-APIC-edge      ata_piix
 15:      43951   IO-APIC-edge      ata_piix
 16:      20099   IO-APIC-fasteoi   uhci_hcd:usb2, yenta, eth0, radeon@pci:0000:01:00.0
 17:      13460   IO-APIC-fasteoi   uhci_hcd:usb3
 18:         28   IO-APIC-fasteoi   uhci_hcd:usb4
 19:          3   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5
 21:     241984   IO-APIC-fasteoi   ath
 22:        255   IO-APIC-fasteoi   Intel ICH6
NMI:          0   Non-maskable interrupts
LOC:     148431   Local timer interrupts
SPU:          0   Spurious interrupts
CNT:          0   Performance counter interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         11   Machine check polls
ERR:          0
MIS:          0
```I have a usb mouse connected and wireless but i'll switch off wireless and give it a go again. I tried booting with a 9.04 cd (can't find my 9.10 cd) last night and ran the system sound tests but they didn't produce any sound either

---

### Post by tgalati4 on 2010-03-14
The fact that you only have 256 ICH6 interrupts is a clue.  Normally that chip is very active.  Especially if you are streaming music.  Also, because the live CD didn't produce any sound points to a hardware failure.

And you double-checked your BIOS to make sure that sound was enabled.

Install tpfan and run it.  See what temperature your southbridge is running at.  Mine runs at 50-53C normally.  If your chip is toasty, then that could indicate that some of those transistors are now resistors.  So instead of sound, you are getting heat.  Listen with headphones to see if you can detect any hiss or pops.  Normally you will get some hiss at max volume, but any weirdness at lower volumes could indicate a meltdown of the audio portion.

sudo apt-get install tpfan
tpfan-admin

---

### Post by airbuntu on 2010-03-17
I've checked my interrupts intermittently and can see that it's not always that low... now it's around 700 and before was around 900...

also checked the temps and can't see anything above 50/55 degrees... and also can't hear anything at all... no hissing ... no blips or anything at all... :(

---

### Post by Yellow Pasque on 2010-03-17
Try a liveCD of some other Linux to test for hardware failure.

---

### Post by blackhawkover on 2010-03-18
I had a sound issue after updating, restarting worked. Fully different system, but being calm and collected helps a lot before you try to make huge system changes and wiping your bios or anything like that. "i'm pullin for ya. We're all in this together" -Red Green.

---

### Post by tgalati4 on 2010-03-19
Download floppy-disk (remember those) diagnostics from IBM for T4X series.  I think it contains a sound check.

---

### Post by matt2909 on 2010-04-14
I also had the problem you have on your thinkpad t43. Have you tried pressing the up/down volume keys above the keyboard? I know it sounds lame, but it fixed my problem. Unfortunately they seem to interact with the hardware separately to the software controls, so you can't see if the mute on the hardware is on or not. 

Hope this helps you out!

---

