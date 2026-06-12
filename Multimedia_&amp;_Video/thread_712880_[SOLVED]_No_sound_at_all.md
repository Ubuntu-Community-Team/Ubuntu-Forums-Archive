---
title: "[SOLVED] No sound at all"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by 4l13n666 on 2008-03-02
Hello,

I have been trying for one week now to get my sound to work on my **Ubuntu 7.10 Gutsy** Gibbon with no success. I am using a **HP Pavillion dv6500** which has the "blue quick launch" buttons under the screen to access and control media easily. Amongst these buttons, there is a mute button. This button is red, which means that its in mute mode. When i press it the sound mutes and unmutes on the screen but the button itself remains red. 

**By running the "lspci"  command in the terminal, i got the following result for my audio device:**

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

My alsamixer is at version 1.0.14.

I have neither any system sounds, or music sounds. Which means i cannot hear any songs or hear **anything whatsoever**.

I have all the basic sound devices that comes with installing **Ubuntu Gutsy Gibbon 7.10,** plus one recently installed in an attempt to fix the sound problem. **No success so far.**

How can i make my sound work?

**Here is my output of the "lspci -v" command in the terminal**


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
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at f8404800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 23
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
        Prefetchable memory behind bridge: 00000000a4000000-00000000a40fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
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
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
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
        Memory at a4100000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 5
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
        [virtual] Expansion ROM at a4000000 [disabled] [size=128K]
        Capabilities: <access denied>

07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at f8100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 18
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

I have tried back and forth with every single tips i have recieved, and trust me, there have been plenty. But no success!

What i need is a **VERY** detailed guide in how to make my sound work.

All the best,
Erik

---

### Post by erginemr on 2008-03-02
Hi Erik,

Now that you have been working on this problem for a week, you may have found this thread already:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

If not, it is a very promising thread with a lot of success stories.

---

### Post by erginemr on 2008-03-02
Otherwise, I can also suggest you to follow:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

**No no, you should try this first, because it matches your card model!**

Good Luck...

---

### Post by 4l13n666 on 2008-03-02
Thank you so much mate!!

Now my sound is working perfectly! I don't know how to thank you! Literally how do i thank people in posts? :P

Also, do you know the command to get the advanced desktop settings manager? The one that makes me have a cube as a deskop when enabled.

---

### Post by erginemr on 2008-03-02
Great news! Now, have fun with your beloved system! :-D

But which link has solved your problem? This is important for other people who will visit your thread later on.

**To close a thread** -> Select "mark this thread as solved" from the thread tools menu.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

**To thank someone** -> Click on the blue ribbon/badge on the bottom right part of the post(s), whose author(s), you believe, has helped you fix your problem.

I will check out the desktop cube issue now...

---

### Post by erginemr on 2008-03-02
For the desktop cube:
[http://ubuntuforums.org/showpost.php?p=4227568&postcount=3](http://ubuntuforums.org/showpost.php?p=4227568&postcount=3)
[http://ubuntuforums.org/showpost.php?p=3840837&postcount=4](http://ubuntuforums.org/showpost.php?p=3840837&postcount=4)
Make sure you have 4 virtual desktops (bottom right corner of your screen).

For the latest version of Compiz Fusion:
[http://ubuntuforums.org/showpost.php?p=4364190&postcount=16](http://ubuntuforums.org/showpost.php?p=4364190&postcount=16)
[http://ubuntuforums.org/showpost.php?p=4238384&postcount=4](http://ubuntuforums.org/showpost.php?p=4238384&postcount=4)

Take Care ):P

---

### Post by 4l13n666 on 2008-03-02
> **erginemr said:**
> Great news! Now, have fun with your beloved system! :-D

But which link has solved your problem? This is important for other people who will visit your thread later on.

**To close a thread** -> Select "mark this thread as solved" from the thread tools menu.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

**To thank someone** -> Click on the blue ribbon/badge on the bottom right part of the post(s), whose author(s), you believe, has helped you fix your problem.

I will check out the desktop cube issue now...

Well, the second link that you told me to try first solved it. I just follower the instructions, rebooted, and viola! It works! Thanks so much!

---

