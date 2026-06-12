---
title: "[SOLVED] Sound problem - worked fine after upgrading then..."
date: 2008-08-03
forum: Multimedia Software
---

### Post by JohnDorian on 2008-08-03
Hi,
I upgraded to Hardy with no problems.  Then last week I got the icon indicating there were updates for me to apply.  Given that I've never had a compatibility issue resulting from such updates over the past 13 months I didn't pay attention to what it was updating.

After applying the update I got a red "X" over the speaker icon.  Hovering over it gives the message "Mixer cannot be found".  See attached screenshots and below output based on the steps from the sticky post.  Needless to say, my situation has not been resolved.

I've followed the advice from the following sticky post in this section.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

brett2@office:~$ aplay -l
aplay: device_list:205: no soundcards found...


lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at ff00 [size=8]
        I/O ports at fe00 [size=4]
        I/O ports at fd00 [size=8]
        I/O ports at fc00 [size=4]
        I/O ports at fb00 [size=16]
        Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
        Expansion ROM at fdf80000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Memory at fe02b000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f900 [size=16]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: fdc00000-fdcfffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2a27
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 5
        Memory at fe02a000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series] (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 5
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at ee00 [size=256]
        Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at fde00000 [disabled] [size=128K]
        Capabilities: <access denied>

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at dc00 [size=256]
        Memory at fddff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 20
        Memory at fddfe000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at df00 [size=128]
        Capabilities: <access denied>

02:09.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 10)
        Subsystem: Linksys EG1032 v3 Instant Gigabit Network Adapter
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at da00 [size=256]
        Memory at fddfd000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at fdc00000 [disabled] [size=128K]
        Capabilities: <access denied>


""A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot""

---

### Post by hansdown on 2008-08-03
Hi johndorian. There is a solved thread that may help. Scroll down,because the english part starts in the second post.
[http://ubuntuforums.org/showthread.php?t=365342&page=2](http://ubuntuforums.org/showthread.php?t=365342&page=2)

---

### Post by montgoss on 2008-08-03
I have the same problem (worked fine, then suddenly nothing after an update).  But I don't have the same sound card.

Relevant portion of lspci:```
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7390
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at f9ff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping
```

"cat /proc/asound/cards" says "--- no soundcards ---".  Any ideas?

Edit: I guess I should say that I too removed and re-installed Alsa with no change, just like the OP.

---

### Post by JohnDorian on 2008-08-03
hansdown - tried it, no luck.

Montgoss - I have the same results as you: "cat /proc/asound/cards" says "--- no soundcards ---"

---

### Post by hansdown on 2008-08-03
Hi again. I believe this is due to the recent foxconn problem. [http://digg.com/linux_unix/Foxconn_releases_test_BIOS_fixing_Linux_crashers](http://digg.com/linux_unix/Foxconn_releases_test_BIOS_fixing_Linux_crashers)
There was a post by a foxconn developer in the last couple of days promissing a fix.
Here is the post.  [http://ubuntuforums.org/showthread.php?t=877721](http://ubuntuforums.org/showthread.php?t=877721)

---

### Post by montgoss on 2008-08-04
I don't see the connection.  Everything was working great with this Ubuntu install for months.  Then an update a few days ago broke a lot of stuff.  My BIOS didn't change.

I posted this elsewhere, but JohnDorian, try this:```
sudo modprobe snd-hda-intel
```

---

### Post by JohnDorian on 2008-08-04
Here's my results from the below code:
FATAL: Module snd_hda_intel not found.


I posted this elsewhere, but JohnDorian, try this:```
sudo modprobe snd-hda-intel
```[/QUOTE]

---

### Post by montgoss on 2008-08-04
Sorry.  I got my threads confused.  You have an ATI audio controller. So, look for snd-ati or something similar.  You should be able to use the tab completion to see your options.  Type "sudo modprobe snd" and then hit tab a few times.  There's a snd-ac97-codec.  Or maybe snd-atiixp?  Sorry, I'm not sure which module is appropriate for your sound card.

---

### Post by JohnDorian on 2008-08-04
lol - I was wondering about that but am willing to try anything!  I'll retry tonight after work.  Thanks for the followup

---

### Post by JohnDorian on 2008-08-04
Here's what I got, which was unexpected:

brett@office:~$ sudo modprobe snd
.adobe/                    .gconfd/                   Pictures/
.bash_history              .gnome2/                   .profile
.bash_logout               .gnome2_private/           Public/
.bashrc                    .ICEauthority              .qt/
.config/                   .kde/                      .sudo_as_admin_successful
.dbus/                     .kde4/                     .synaptic/
.DCOPserver_office__0      .kpackage/                 Templates/
.DCOPserver_office_:0      .local/                    Videos/
Desktop/                   .macromedia/               .Xauthority
.directory                 .mcop/                     .xine/
.dmrc                      .mcoprc                    .xsession-errors
Documents/                 .mozilla/                  .xsession-errors-:2
.gconf/                    Music/

---

### Post by JohnDorian on 2008-08-04
Sorry to say but nothing worked so i took advantage of having my /home in a separate partition and did a fresh install of hardy. 

Seems like this is a prevalent problem, one that doesn't appear to have a solution other than 'start over'.  

No problems now, here's the output of aplay -l

brainey@office:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

