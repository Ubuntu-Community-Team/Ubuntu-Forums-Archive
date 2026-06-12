---
title: "Cannot display this video mode = no grub"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by imacQ on 2011-04-14
Natty live worked fine on Dell Optiplex GX 150 (xp, fedora, lubuntu) and installed without problems as fourth OS. Monitor = older 17" Dell LCD. However, upon boot grub does not show up. What shows up is black screen with "Cannot display this video mode." After about 15 seconds, the machine boots into Natty. Also upon shutdown or restart there is brief display on the monitor of "Cannot display this video mode," after which the machine proceeds to shutdown or restart without problems except the aforementioned. 

I can't see Grub, thus I can't select a different OS.

I uncommented from the /etc/default/grub GRUB_GFXMODE, and added more resolutions, but no joy. 

Advice appreciated. Off to work will see what you've got to say later. Thanks

---

### Post by dino99 on 2011-04-14
how many grub installed ? which is the master ?
unselect automatic login if you have it done

if you have a xorg.conf, remove it

---

### Post by imacQ on 2011-04-14
Fedora 15 old grub was the main grub. i overwrote the MBR with Natty Grub2. When i run update-grub Grub2 does see all distros. 

I'm not using automatic login. 

More suggestions/ideas are welcome. Thanks.

---

### Post by MAFoElffen on 2011-04-14
> **imacQ said:**
> Natty live worked fine on Dell Optiplex GX 150 (xp, fedora, lubuntu) and installed without problems as fourth OS. Monitor = older 17" Dell LCD. However, upon boot grub does not show up. What shows up is black screen with "Cannot display this video mode." After about 15 seconds, the machine boots into Natty. Also upon shutdown or restart there is brief display on the monitor of "Cannot display this video mode," after which the machine proceeds to shutdown or restart without problems except the aforementioned. 

I can't see Grub, thus I can't select a different OS.

I uncommented from the /etc/default/grub GRUB_GFXMODE, and added more resolutions, but no joy. 

Advice appreciated. Off to work will see what you've got to say later. Thanks
Strange... The manual says by default- "if" grub2 didn't see any other OS'es, then you would see no grub2 menu as it would automatically boot into the sole OS.

But-- The user can interrupt the boot process and display the menu by holding down the SHIFT key until the menu displays. GRUB  2 searches for a depressed SHIFT key signal during boot. If the key is  pressed or GRUB 2 cannot determine the status of the key, the menu is  displayed.  Although the GNU Grub2 manual on this version says that the function watching for this key is disabled when there are muliple OS'es present in the menu... but it's worth a try, right?

A few things... First, this version of Grub2 is a GNU Release Candidate (v1.99~rc1).  There are a few bugs yet (I am affected by a few.)

Second in etc/default/grub... try adding a # character (comment) in front of the line containing GRUB_HIDDEN_TIMEOUT=0  and see if it displays...

Third, the GRUB_GXFMODE.  Yes, they are testing graphics changes heavily in this beta version of Ubuntu and in this version of Grub..  Yes, uncommenting that line in the /etc/default/grub "should" work... If no setting is found in */etc/default/grub*, Grub2 uses the resolution established in */etc/grub.d/00_header*, which is set at 640x480. Doesn't your PC have Intel DVMT graphics?   That should be supported natively... 

Another way you might try is to add more modes by separating them with a semi-colon such as describes here in the GNU Grub2 manual:
```
**13.1.8 gfxmode**  If this variable is set, it sets the resolution used on the ‘gfxterm’ graphical terminal.  Note that you can only use modes which your graphics card supports via VESA BIOS Extensions (VBE), so for example native LCD panel resolutions may not be available.  The default is ‘auto’, which selects a platform-specific default that should look reasonable.     
The resolution may be specified as a sequence of one or more modes, separated by commas (‘,’) or semicolons (‘;’); each will be tried in turn until one is found.  Each mode should be either ‘auto’, ‘widthxheight’, or ‘widthxheightxdepth’.  

```You can find those modes either by using "sudo hwinfo --framebuffer" from a terminal session or if you are really trying to find out what is going on in Grub while in Grub, when you get the Grub Menu to display, press "c" and drop down to the Grub CLI (command line interface...

At the Grub command line you can use this commands to query and test video modes:
```
GRUB>  vbeinfo
GRUB > vbetest
GRUB> videotest
```Get ready with your "pause" key as 3 screens of info will go by faster than you can possibly read.  When ready to read more, hit the enter key.  vbetest will tell you what video mode in hex it is currently set to.  videotest will test the video subsystem by displaying colored boxes.

But still, while you are in the Grub CLI-- instead changing things (hard edits) and rebooting to see if it worked... Just just *set* and *reset* to change your environment variable from the command line.  Such as to set the screen resolution, you should set the variable $vbe_mode before loading vbe and/or gfxmterm (default mode is 0x101 i.e. 640x480 8bpp) Test your graphics... Or ```
Set GRUB_GFXMODE=640x480
``` or whatever.

---

### Post by imacQ on 2011-04-16
dino99 and MAFoElffen, thanks for responding.
 
I've tried all suggestions, and I have reinstalled grub. Nothing working yet. 

I wonder if someone can decipher this clue, or if it is a clue? 
[QUOTE=imacQ;10675983] Also upon shutdown or restart there is brief display on the monitor of "Cannot display this video mode," after which the machine proceeds to shutdown or restart without problems except the aforementioned.

Since it's occurring at shutdown as well as pre grub, could it be something other then grub? What process runs between bios and grub? Nothing? I don't know. What process runs right after shutdown?

Including lspci: 
```
OptiPlex-GX150:/etc/X11$ lspci -v
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
	Subsystem: Dell Device 00be
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 04) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 00be
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 9
	Memory at f0000000 (32-bit, prefetchable) [disabled] [size=64M]
	Memory at fe000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: f4000000-f7ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 11) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 11) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ff80 [size=32]
	Kernel driver in use: uhci_hcd

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 11)
	Flags: medium devsel, IRQ 10
	I/O ports at dcd0 [size=16]
	Kernel modules: i2c-i801

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 11) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at ff60 [size=32]
	Kernel driver in use: uhci_hcd

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 11)
	Subsystem: Dell Device 00be
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at d800 [size=256]
	I/O ports at dc40 [size=64]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:07.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Rage 128 AIW
	Flags: stepping, medium devsel, IRQ 9
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	I/O ports at ec00 [size=256]
	Memory at fcffc000 (32-bit, non-prefetchable) [size=16K]
	Expansion ROM at 80000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: aty128fb

01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
	Subsystem: Dell Device 00be
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at e880 [size=128]
	Memory at fcffbc00 (32-bit, non-prefetchable) [size=128]
	Expansion ROM at fd000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x
```

---

### Post by terry_gardener on 2011-04-16
i have had this problem with one of my pcs but my monitor displayed out of range instead which i think means the same thing. 

to solve the problem i installed startup manager and changed the following setting to:
display resolution 1024x768
color depth 16 bit 

and under the advanced tab 

bootloader 1024x768

clicked close and this updates the grub files for you.

---

### Post by imacQ on 2011-04-16
terry_gardner,
thank you. That did the trick! 

Could not see the forest for the trees. So simple, while I blindly "saw" it as complex.

---

### Post by MAFoElffen on 2011-04-16
> **terry_gardener said:**
> i have had this problem with one of my pcs but my monitor displayed out of range instead which i think means the same thing. 

to solve the problem i installed startup manager and changed the following setting to:
display resolution 1024x768
color depth 16 bit 

and under the advanced tab 

bootloader 1024x768

clicked close and this updates the grub files for you.
Mentioned above as chages to grub, , but done through this app.  Changing those options in the startup-manager app changes the /etc/grub.d/00_header file, line that says set gfxmode=auto to "set gfxmode-1024x768" and then add/appends vga-758 to the kernel boot line in 10_linux section...

---

