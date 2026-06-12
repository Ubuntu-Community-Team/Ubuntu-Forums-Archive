---
title: "Fade out."
date: 2009-11-30
forum: Multimedia Software
---

### Post by krymz on 2009-11-30
Hello. i will make this short and to the point. i want to get rid of windows in an attempt to become more and more "sustainable". i have had some "basic" training of windows vista in a HP phone support, but i still dont know anything about coding or "less common" terms like kernel and whatnot. also, my machine came with a 64 dual core but a 32 bit system. so i installed the 64 bit version of Ubuntu.

so i download the 9.10 package, install it as dual OS to choose when u boot. it looks nice and all but i dont start playing with it yet. the same day, someone tells me to get MINT because its more noob friendly. i uninstall 9.10, install mint, and and i cant log in cause my wireless keyboard and mouse are not detected....so i uninstall mint and reinstall 9.10. 

during reinstalation, my GF ***** around with the powerbar and turns the master switch on and off a bunch of times... so i think i uninstalled and reinstalled ubuntu 2 or 3 aditional times, in diferent ways (from windows with an deamon tool, from a burned cd (i think i installed it twice too!, once from windows, and then again from then CD when the bios boots from the cd and i think i reinstalled it instead of going straight to the already instaled ubuntu....when i get the OS choosing screen, 

i got ubuntu version 

ubuntu, linux 2.6.31-15- generic
ubuntu, linux 2.6.31-15- generic (recovery mode)
ubuntu, linux 2.6.31-14- generic
ubuntu, linux 2.6.31-14- generic (recovery mode)
memory test (mem test86+)
memory test (mem test86+, serial console 115200)
dell utility partition (on/dev/sda)
windows vista (loader) (on/dev/sd3)

but im writing for this very troublesome issue. when theres a constant sound going on (music player, youtube, ect) the sound fades out in a few seconds.
ive been trying to fix it trough google searches and dint seem to make any progress. i uninstaled that ALSA or whatever thats called, and i think i just reinstalled it but it still does the fadding effect without being asked to do it. i dont understand a lot of what i would see in the replies to the people who asked for help, they would ask stuff like "check if your SDFSBB  and check if your gjdovihf are working in sdajfsdffg mode. (random letter acronym representing my lack of knowing what the accronims are suposed to be) without a clear "type these commands in order, nothing to tell when a coding line stops or if your suposed to use the line or whatever....

so in resume;
i got ubuntu 9.10, and my sounds fade out. i need help. im going to try to get to IRC but i would like help here too so that if my IRC window crashes i dont loose all the help ;)

heres the last lines of code i put in terminal just now, i gave up on self help i cant find noob friendly enough directives

> philippe@pac:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
philippe@pac:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
philippe@pac:~$ Lspci -v
No command 'Lspci' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
Lspci: command not found
philippe@pac:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    Subsystem: nVidia Corporation C51 Host Bridge
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
    Subsystem: nVidia Corporation C51 Memory Controller 0
    Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
    Subsystem: nVidia Corporation C51 Memory Controller 1
    Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
    Subsystem: nVidia Corporation C51 Memory Controller 5
    Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
    Subsystem: nVidia Corporation C51 Memory Controller 4
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    Subsystem: nVidia Corporation C51 Host Bridge
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
    Subsystem: nVidia Corporation C51 Memory Controller 3
    Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
    Subsystem: nVidia Corporation C51 Memory Controller 2
    Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00008000-00008fff
    Memory behind bridge: fda00000-fdafffff
    Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f6000000-f9ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
    Subsystem: Dell Device 01ed
    Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
    Subsystem: Dell Device 01ed
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at 1c00 [size=64]
    I/O ports at 1c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
    Subsystem: Dell Device 01ed
    Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
    Subsystem: Dell Device 01ed
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
    Subsystem: Dell Device 01ed
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell Device 01ed
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at e000 [size=16]
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell Device 01ed
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at 09e0 [size=8]
    I/O ports at 0be0 [size=4]
    I/O ports at 0960 [size=8]
    I/O ports at 0b60 [size=4]
    I/O ports at cc00 [size=16]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: fdc00000-fdcfffff
    Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
    Subsystem: Dell Device 01ed
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

03:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
    Subsystem: eVga.com. Corp. Device c958
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f6000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at bc00 [size=128]
    [virtual] Expansion ROM at f9000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
    Subsystem: Dell Device 01ed
    Flags: bus master, fast devsel, latency 64, IRQ 19
    Memory at fddfe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: b44
    Kernel modules: b44 

---

### Post by krymz on 2009-12-01
bump:popcorn:

---

### Post by krymz on 2009-12-03
sticker to bumber

---

### Post by laeg_ on 2009-12-08
I have the exact same problem after following the Ubuntu docs verbatim [here]("https://help.ubuntu.com/community/RestrictedFormats/Flash#Troubleshooting") and this [Comprehensive Multimedia & Video Howto]("https://help.ubuntu.com/community/RestrictedFormats/Flash#Troubleshooting") taking the Gecko route, although I'm not suggesting one or the other of the documents is the cause of the problem, merely outlining what I've tried so far.

---

### Post by krymz on 2009-12-08
well whatever. i now have 2.0gig of free space on my drive, all of this for a useless Oss thats not at all "intuiative" and . i had so much hope, but all i experienced was 2 minutes of "wow cool" and an infinity of "WTFFFFFFFFFFF!@@!@!@!@!"

i thought well screw the sound lets try installing a game i like that was suposed to be made for linux or something in the same spirit, and it would get stuck updating, 10 times out of 10. and thats after an eternity of trying to figure out how to use the installer that i had downloaded, wich required some more unknowed coding, and then i could not even find the stupid luach buton (it was openable from the taskbar into the game folder, put itself there on its own, but there wasent anything to lauch it from any of the game files.

what pissed me off the most was putting in coding that was absolutly not "self figurable" in the whatever thing that looks like MSdos or the like.

maybe you should advertize this **** better instead of making it sound so nice and wonderfull

---

