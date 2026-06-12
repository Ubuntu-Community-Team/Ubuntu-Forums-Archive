---
title: "Ubuntu Karmic Low Resolution HP Compaq D530"
date: 2009-12-18
forum: Multimedia Software
---

### Post by Compist on 2009-12-18
Hi all,

I'm fairly new to Ubuntu and the world of Linux, and was, until yesterday, having a great time with the OS.
After moving the computer due to me finally getting a wireless keyboard, I was dismayed at booting it up and finding that it was outputting at 800x600.  It's AWFUL.  I hate having to scroll sideways just to look at all of a webpage for example.
The computer itself is a HP Compaq D530 SFF, which I think uses Intel Onboard Graphics.  The computer is not modified in any way from the factory except for some extra RAM.  It's connected to a 32" LCD Vistron TV, which in PC mode acts like any other monitor.
After some playing around, and learning that, annoyingly, xorg.conf doesn't apply to karmic (so nobody suggest sodding "sudo dpkg-reconfigure xserver-xorg" because on karmic it DOESNT WORK and just leaves the terminal gorming at you), I realised that the system didn't seem to have the correct EDID.  Some further digging and running sudo get-edid outputted this;

get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x2110 "Intel(r)865G Graphics Chip Accelerated VGA BIOS"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed

The EDID data should not be trusted as the VBE call failed
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;N&#65533; F'x&#65533;    &#65533;&#65533;UF&#65533;$IK/&#65533;&#65533;&#65533;f!P&#65533;Q08p&#65533;&#65533;!&#65533;1
           &#65533;<K0<

      &#65533;32"W VGA

Now, there's all sorts of work arounds for this and I tried every single one I could find, to no avail.  The GUI Display Tool (System > Preferences > Display) still indentifies the monitor as "unknown" and only gives 640x480 and 800x600 options.
I've learned through much digging that this probably doesn't work as the task of handling the EDID is now handed off the kernel via something called KDM, which is supposed to make things faster.  All it's done so far is turn a perfectly good system into an annoyingly configured one.

I've formatted the computer and reinstalled ubuntu, and it STILL doesnt fix things.
My guess is that between me moving the machine and this problem occuring, the monitors EDID became corrupt.  So what the hell should I do now? :(

I should also mention that I hooked a Samsung Windows XP netbook to the same monitor and it outputted in 1024x768 with no problem whatsoever.

Has anyone got any ideas on how to get my ubuntu machine to do the same?

Compist

---

