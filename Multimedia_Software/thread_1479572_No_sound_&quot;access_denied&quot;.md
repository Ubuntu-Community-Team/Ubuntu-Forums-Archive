---
title: "No sound &quot;access denied&quot;"
date: 2010-05-10
forum: Multimedia Software
---

### Post by ubunterooster on 2010-05-10
```
 ubunterooster@Rooster:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
ubunterooster@Rooster:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Flags: bus master, 66MHz, medium devsel, latency 32
    Memory at <ignored> (64-bit, non-prefetchable)
    Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
    Flags: bus master, 66MHz, medium devsel, latency 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fde00000-fdffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
    I/O ports at ff00 [size=8]
    I/O ports at fe00 [size=4]
    I/O ports at fd00 [size=8]
    I/O ports at fc00 [size=4]
    I/O ports at fb00 [size=16]
    Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe02c000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    Memory at fe029000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
    Subsystem: Giga-byte Technology Device 4385
    Flags: 66MHz, medium devsel
    Capabilities: <access denied>
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Giga-byte Technology Device 5002
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at fa00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
[COLOR=Black]
[/COLOR] [COLOR=Black]00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller[/COLOR] [COLOR=Black]
    Subsystem: ATI Technologies Inc SB700/SB800 LPC host controller
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)[/COLOR] [COLOR=Black]
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fdc00000-fdcfffff
    Prefetchable memory behind bridge: fdb00000-fdbfffff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)[/COLOR] [COLOR=Black]
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe028000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration[/COLOR] [COLOR=Black]
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map[/COLOR] [COLOR=Black]
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller[/COLOR] [COLOR=Black]
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control[/COLOR] [COLOR=Black]
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control[/COLOR] [COLOR=Black]
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200][/COLOR] [COLOR=Black]
    Subsystem: Giga-byte Technology Device d000
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at ee00 [size=256]
    Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
    Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200][/COLOR] [COLOR=Black]
    Subsystem: Giga-byte Technology Device 960f
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Realt[/COLOR] ek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: Giga-byte Technology Device e000
    Flags: bus master, fast devsel, latency 0, IRQ 26
    I/O ports at de00 [size=256]
    Memory at fdaff000 (64-bit, prefetchable) [size=4K]
    Memory at fdae0000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at fda00000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:07.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)
    Subsystem: Belkin Device 0001
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at fdcff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

03:07.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10)
    Subsystem: Belkin Device 0001
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at fdcfe000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

03:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20)
    Subsystem: Belkin Device 0002
    Flags: bus master, medium devsel, latency 32, IRQ 23
    Memory at fdcfd000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
    Subsystem: Giga-byte Technology Device 1000
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at fdcfc000 (32-bit, non-prefetchable) [size=2K]
    Memory at fdcf8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

ubunterooster@Rooster:~$ 
  
```I can't figure out why it is dead silent and why I get "access denied" in "capabilities" or why I get no sound.

---

### Post by ubunterooster on 2010-05-10
followed [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) as I was but decided ,once I got stuck figuring out what the carrd was to get on the site he linked, to start a thread. Messing around a while I decided to not follow the instructions completely. > 
[LEFT]**_[SIZE=2]Using alsa-source[/SIZE]_**[/LEFT]

[LIST=1]
[*][LEFT][SIZE=2]Type  the following to shell: (note: module-assistant is optional, it will  compile the package for you)     Code:
     sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source 
[/SIZE][/LEFT]
[*][LEFT][SIZE=2]     Code:
     sudo dpkg-reconfigure alsa-source 
[/SIZE][/LEFT]
[*][LEFT][SIZE=2]You now have a big blue dialog box  (left and right keys to choose 'Yes' and 'No', Enter key proceed).  Answer yes (for ISA-PNP - recommended by package maintainers), then yes  again (for debugging - recommended by package maintainers).[/SIZE][/LEFT]
[*][LEFT][SIZE=2]Now you must pick which driver you  want to install. Use space to select and deselect modules, and up and  down to navigate.[/SIZE][/LEFT]
[*][LEFT][SIZE=2]From **General Help step 3**,  you should know the name of your driver. Deselect 'all' (the * will go  away), and select your driver. In my case, I deselected 'all' then  selected 'via82xx'. Hit Enter. Almost home free![/SIZE][/LEFT]
[*]
[LIST]
[*][LEFT][SIZE=2]**If you chose  module-assistant**      Code:
     sudo module-assistant a-i   alsa-source 
 If the progress bar reaches 100% with no errors, you will have  installed the drivers successfully.[/SIZE][/LEFT]
[/LIST]
 
[/LIST]

[LIST=1]
[*]
[LIST]
[*][LEFT][SIZE=2]On 5 I left "all" selected. IT WORKS!!! WOOOOOT!!!! It's 'bout bedtime and I just relish ending the day on a good note such as this. :D[/SIZE][/LEFT]
[/LIST]
Though I am courious as to the reason for all of the "access denied"s
[/LIST]

---

### Post by ubunterooster on 2010-05-11
It's happening again :confused: ```
ubunterooster@Rooster:~$  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: [COLOR=red]ALC889A Analog[/COLOR] [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: [COLOR=red]ALC889A Digital[/COLOR] [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ubunterooster@Rooster:~$  
```I retried step 5 looking for any "alc889a" modules. but found none. Back to square one, I guess.

I would like it if there is a way to get it to work right; failing that, some recommendations on sound cards that are at least 5.1 analog (not digital as I use analog-style speakers)

---

### Post by ubunterooster on 2010-05-11
update: Freaky how I get the funny "bibibibong" as usual on logout and KDE has sound, but not Gnome, gnome+openbox, Lxde, lubuntu, xfce, openbox...and I can't use KDE!! So I get it when their is no DE loaded (KDE does not load properly) but when I have my DE I have no sound. :?:

---

### Post by ubunterooster on 2010-05-11
Do'uh. Ubuntu was trying to use the digital output, I just went to system>preferences>sound>Hardware  and choose the analog as opposed to digital output. But then what do you expect from a Rooster, LOL. G'bye for now; I have to catch up on listening to my music :D :D :D :D

---

