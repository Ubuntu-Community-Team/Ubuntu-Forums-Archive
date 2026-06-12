---
title: "No sound on HP Laptop"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by virtualcoder on 2008-01-30
hi,

  Ive got no sound since I installed ubuntu 7.10 64 bit, and Ive tried different solutions on the web but none worked for me.
  My laptop is a HP Pavilion 6699ee, and Ive got everything else to work with ubuntu except sound, so please help!

  I'm not sure which sound card is installed but Vista seems to have the following driver installed on my machine : "Realtek High definition audio".

I've compiled the alsa libraries as well as play with the settings of:
System->Preferences->Sound
I've also gone in alsa mixer to unmute anything muted.

It seems to me as a bug cause I've tried a lot of things except post any message about it, so before I go about posting a bug on launchpad, I decided to post it here.

I'm not sure if ubuntu is even detecting and listing my sound card as shown is the lists below:

The output of aplay -l is:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The output of lspci -v is:

lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
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
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f8404800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00004000-00007fff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f3ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00008000-0000bfff
        Memory behind bridge: bc000000-bfffffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000cbffffff
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: f8000000-f80fffff
        Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f8404c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
        Memory behind bridge: f8100000-f81fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 18d8 [size=8]
        I/O ports at 18cc [size=4]
        I/O ports at 18d0 [size=8]
        I/O ports at 18c8 [size=4]
        I/O ports at 18e0 [size=32]
        Memory at f8404000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: medium devsel, IRQ 10
        Memory at 88100000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation PRO/Wireless 3945BG Network Connection
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at c000 [size=256]
        Memory at f8000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <access denied>

07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at f8100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at f8100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8101000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8101400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by virtualcoder on 2008-01-30
Please give some ideas cause I've tried everything I've found on the web and I dont want to loose hope.
I'm also kind of new to linux being on my home computer and completely new to Ubuntu, although I've had it installed for about 1 1/2 months.

---

### Post by virtualcoder on 2008-01-30
Heres some more info:

/usr/src$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ID 268
Codec: Motorola Si3054

---

### Post by virtualcoder on 2008-01-31
please someone give some response!

---

### Post by fpscott on 2008-02-23
I hope I'm not too late, since I just found the answer myself today, after getting reading to uninstall Linux for good, and going back to Vista and OS X. Here's the answer I gave in another part of the forum:

[B]What worked for me with my HP Pavilion DV9700 laptop, and also for a friend with a Dell laptop with the same problem, was to open terminal and type the following line. You'll be asked for your root password. After this finishes installing, reboot your computer, and you should have sound. Good luck!

sudo apt-get install linux-backports-modules-generic

Frank
[/B]

---

### Post by virtualcoder on 2008-03-06
Thanks fpscott,

 I dont remember if I tried that before but I just tried it right now, and like every other option I've found, it doesnt seem to do the job.
I gave up on trying to get sound since I've probably tried every option available on the web.

Using a computer without sound seems like you are stuck in some kind of endless pit, its a  sick feeling.

I'm using ubuntu only if i really need to otherwise, ive got three other operating systems (xp, vista, mac) that work just fine.

But I really, really wanted to use a linux operating system, and ubuntu seemed to be very popular, so I will go ahead and report a bug. Lets see what happens.

---

### Post by virtualcoder on 2008-03-06
Well i guess my sound card is a Realtek ID 268.

Also for some funny reason, I loose my wireless connection from time to time, and sometimes it becomes so stubborn that it wont allow me to connect unless i restart my computer.

---

### Post by gviamont on 2008-03-31
I saw this potential solution on another thread:
[http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

Apparently 7.10's auto-detect feature doesn't always work on every system, and manually setting the sound device by trying every possibility in the list has worked for some people  It sounds like you've tried a lot of things though, so apologies if you've already given this a shot.

By the way, the solution of installing the package linux-backports-modules-generic and then rebooting did make sound come up finally on my hp dv9700.  It does sound overly simple in that steps are being left out, but literally those are the only two steps I took.  I didn't even toggle the physical mute button on my laptop.  My guess is that if this didn't work on your machine it's probably not the solution for your system. 

Out of curiosity have you tried upgrading to beta Hardy?  I guess it's supposed to go stable later in April, but it may be worth a shot as a last ditch effort.  There's a nice howto on the forums for going from Gutsy 7.10  to Hardy beta 8.04.  I've tried it myself, and it was pretty straightforward.  

Best of luck, and I hope you can get your system fully functional!

---

