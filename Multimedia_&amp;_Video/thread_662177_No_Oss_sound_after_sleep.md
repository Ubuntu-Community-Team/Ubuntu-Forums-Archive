---
title: "No Oss sound after sleep"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by bcn17 on 2008-01-08
First I tried the [Comprehensive Sound Problem guide]("http://ubuntuforums.org/showthread.php?t=205449"). I ran into a dead end because have have ICH8. alsa wasn't going to work. Then Temüjin came to the rescue and offered up a [HOW TO]("http://ubuntuforums.org/showpost.php?p=3768914&postcount=6") for oss. 

Sound works great, and in flash too (after continuing the HOW TO). However, when ever my computer goes to sleep and I wake it back up sound no longer works. However a reboot will fix the problem. Logging out and back in won't fix the problem either. Has to be a reboot.
```
 bar@barubuntu:~$ osstest
Sound subsystem and version: OSS 4.0 (b1011/200712200358) (0x00040003)
Platform: Linux/x86_64 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007

*** Scanning sound adapter #-1 ***
/dev/oss/hdaudio0/pcm0 (audio engine 0): High Definition Audio speaker
- Performing audio playback test... 
<left> Device returned error: Input/output error
/dev/oss/hdaudio0/pcm1 (audio engine 1): High Definition Audio headphone
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/hdaudio0/pcmin0 (audio engine 2): High Definition Audio rec1
- Skipping input only device
/dev/oss/hdaudio0/pcmin1 (audio engine 3): High Definition Audio rec2
- Skipping input only device

*** Some errors were detected during the tests ***
```

Here is some more info.
```
bar@barubuntu:~$ aplay -l


********************   WARNING   *******************************
Warning! aplay uses ALSA emulation instead of the native OSS API
****************************************************************

**** List of PLAYBACK Hardware Devices ****
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 0: OSS ID [High Definition Audio speaker]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 1: OSS ID [High Definition Audio headphone]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 2: OSS ID [High Definition Audio rec1]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 3: OSS ID [High Definition Audio rec2]
  Subdevices: 1/1
  Subdevice #0: OSS subname

```
and..
```
bar@barubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c4000000-c6ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f8404000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f0000000-f3ffffff
        Prefetchable memory behind bridge: 00000000fa000000-00000000fbffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000fc000000-00000000fdffffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Prefetchable memory behind bridge: 00000000c8000000-00000000c9ffffff
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        Memory behind bridge: f8000000-f80fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f8404400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=32
        Memory behind bridge: f8100000-f81fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18a0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 18f8 [size=8]
        I/O ports at 18cc [size=4]
        I/O ports at 18f0 [size=8]
        I/O ports at 18c8 [size=4]
        I/O ports at 18e0 [size=16]
        I/O ports at 18d0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: medium devsel, IRQ 10
        Memory at c7000000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1) (prog-if 00 [VGA])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f0000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1100
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f8000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f8100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

0e:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: bus master, medium devsel, latency 64, IRQ 23
        Memory at f8100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0e:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: medium devsel, IRQ 10
        Memory at f8100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0e:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: COMPAL Electronics Inc Unknown device 0025
        Flags: medium devsel, IRQ 10
        Memory at f8101000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```

I'm using Gutsy Gibbon 64-bit. Also, these commands were entered into the terminal AFTER my computer went asleep and was waken back up. If the computer is freshly rebooted it works great and osstest works fine. If the aplay -l or the lspci -v commands are needed when sounds is working ill post them. THANKS!

---

### Post by bcn17 on 2008-02-08
I just had a random sound failure and had to uninstall and reinstall oss. I downloaded and installed a newer version and unfortunately still no sound after computer goes to sleep and wakes back up.. :( Anyone else have this problem?

---

### Post by Dandeloreon on 2008-02-08
have you tried restarting alsa, and/or oss?

---

### Post by happyhamster on 2008-02-09
- Just a long shot, but you could check (when sound doesn't work):

dmesg | grep irq -i

(It will look in your log for the "irq" string). If you find something like "IRQ ..: Nobody cared" then try booting with the 'irqpoll' parameter.

- Easiest way to do this is to reboot and add the parameter in the grub menu. You usually enter that menu automatically, if not, press the escape key a few times when you see the "grub loading..." message.

- A line called "Ubuntu gutsy, kernel 2.6...." should be highlighted. Press 'e' to edit.
- Select the second line, "kernel /boot/vmlinuz...." and press 'e' again.
- You should see all boot parameters currently used (usually: ro quiet splash).
- Add irqpoll to the end of that list (make sure there's a space between them).
- Leave the other parameters alone, at least always keep "ro".
- Accept with the enter key.
- You're back to the previous page. Boot with the new parameter, by pressing 'b'.
- Check if anything has changed for the better.

- Advantage of this procedure is that it's safe: its' only temporary, because everything will be reset after a reboot. If you're sure that you've found the right parameter, you can make the change permanent by adding it to your menu.lst.

sudo nano /boot/grub/menu.lst

- Search for the correct "kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=........ ro quiet splash" line and add irqpoll at the end (again with a space between splash and irqpoll).
- Reboot.

Good luck, and keep us informed.

---

### Post by bcn17 on 2008-05-01
I'm sorry didn't get around to trying this- however 8.04 alsa works with intel ICH8 out of the box! Yay!

---

