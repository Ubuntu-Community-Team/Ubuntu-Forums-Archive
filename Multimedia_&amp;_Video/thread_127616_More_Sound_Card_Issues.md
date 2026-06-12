---
title: "More Sound Card Issues"
date: 2006-02-09
forum: Multimedia &amp; Video
---

### Post by chageman on 2006-02-09
Hi Far East
as a newbie am trying to get sound to work and have followed your earlier instructions to identify the pci sound chip as follows

dch@Zeus:~$ lspci -v | grep audio
0000:01:08.0 Multimedia audio controller: Rockwell International Riptide PCI Aud io Controller
dch@Zeus:~$

other system has an isa Vibra16 Sound Blaster card and have the isabus.txt file - not sure which "#" to remove from the file and if removing the # from ACY Y will then make the drivers function properly - will post from other system shortly

not sure where or how to go from here to install proper drivers - any assistance would be appreciated

Best regards
cal

---

### Post by chageman on 2006-02-09
here is the isa pnpdump file

# $Id: pnpdump_main.c,v 1.27 2001/04/30 21:54:53 fox Exp $
# Release isapnptools-1.26
# 
# This is free software, see the sources for details.
# This software has NO WARRANTY, use at your OWN RISK
# 
# For details of the output file format, see isapnp.conf(5)
# 
# For latest information and FAQ on isapnp and pnpdump see:
# [http://www.roestock.demon.co.uk/isapnptools/](http://www.roestock.demon.co.uk/isapnptools/)
# 
# Compiler flags:  -DREALTIME -DHAVE_PROC -DENABLE_PCI -DHAVE_SCHED_SETSCHEDULER -DHAVE_NANOSLEEP -DWANT_TO_VALIDATE
# 
# Trying port address 0273
# Board 1 has serial identifier 6d ff ff ff ff f0 00 8c 0e

# (DEBUG)
(READPORT 0x0273)
(ISOLATE PRESERVE)
(IDENTIFY *)
(VERBOSITY 2)
(CONFLICT (IO FATAL)(IRQ FATAL)(DMA FATAL)(MEM FATAL)) # or WARNING

# Card 1: (serial identifier 6d ff ff ff ff f0 00 8c 0e)
# Vendor Id CTL00f0, No Serial Number (-1), checksum 0x6D.
# Version 1.0, Vendor version 1.0
# ANSI string -->Creative ViBRA16X PnP<--
#
# Logical device id CTL0043
#     Device supports vendor reserved register @ 0x38
#     Device supports vendor reserved register @ 0x3b
#     Device supports vendor reserved register @ 0x3c
#     Device supports vendor reserved register @ 0x3f
#
# Edit the entries below to uncomment out the configuration required.
# Note that only the first value of any range is given, this may be changed if required
# Don't forget to uncomment the activate (ACT Y) when happy

(CONFIGURE CTL00f0/-1 (LD 0
#     ANSI string -->Audio<--

# Multiple choice time, choose one only !

#     Start dependent functions: priority preferred
#       IRQ 5.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 1.
#             8 bit DMA only
#             Logical device is a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 1))
#       Next DMA channel 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 1 (CHANNEL 3))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0220
#             IO base alignment 1 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0330
#             Maximum IO base address 0x0330
#             IO base alignment 1 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0330))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0388
#             Maximum IO base address 0x0388
#             IO base alignment 1 bytes
#             Number of IO addresses required: 4
# (IO 2 (SIZE 4) (BASE 0x0388))

#       Start dependent functions: priority acceptable
#       IRQ 5, 7, 9 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Next DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 1 (CHANNEL 0))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0300
#             Maximum IO base address 0x0330
#             IO base alignment 48 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0300))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0388
#             Maximum IO base address 0x0388
#             IO base alignment 1 bytes
#             Number of IO addresses required: 4
# (IO 2 (SIZE 4) (BASE 0x0388))

#       Start dependent functions: priority acceptable
#       IRQ 5, 7, 9 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Next DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 1 (CHANNEL 0))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0300
#             Maximum IO base address 0x0330
#             IO base alignment 48 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0300))

#       Start dependent functions: priority acceptable
#       IRQ 5, 7, 9 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Next DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 1 (CHANNEL 0))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))

#       Start dependent functions: priority functional
#       IRQ 5, 7, 9 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0300
#             Maximum IO base address 0x0330
#             IO base alignment 16 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0300))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0388
#             Maximum IO base address 0x0394
#             IO base alignment 4 bytes
#             Number of IO addresses required: 4
# (IO 2 (SIZE 4) (BASE 0x0388))

#       Start dependent functions: priority functional
#       IRQ 5, 7, 9 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))

#     End dependent functions
 (NAME "CTL00f0/-1[0]{Audio               }")
# (ACT Y)
))
#
# Logical device id CTL7005
#     Device supports vendor reserved register @ 0x38
#     Device supports vendor reserved register @ 0x3b
#     Device supports vendor reserved register @ 0x3c
#     Device supports vendor reserved register @ 0x3f
#
# Edit the entries below to uncomment out the configuration required.
# Note that only the first value of any range is given, this may be changed if required
# Don't forget to uncomment the activate (ACT Y) when happy

(CONFIGURE CTL00f0/-1 (LD 1
#     Compatible device id PNPb02f
#     ANSI string -->Game<--

# Multiple choice time, choose one only !

#     Start dependent functions: priority preferred
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0201
#             Maximum IO base address 0x0201
#             IO base alignment 1 bytes
#             Number of IO addresses required: 1
# (IO 0 (SIZE 1) (BASE 0x0201))

#       Start dependent functions: priority acceptable
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0200
#             Maximum IO base address 0x020f
#             IO base alignment 1 bytes
#             Number of IO addresses required: 1
# (IO 0 (SIZE 1) (BASE 0x0200))

#     End dependent functions
 (NAME "CTL00f0/-1[1]{Game                }")
# (ACT Y)
))
# End tag... Checksum 0x00 (OK)

# Returns all cards to the "Wait for Key" state
(WAITFORKEY)

---

### Post by FarEast on 2006-02-10
Hi;) ,

Thanks for the info.

# Card 1: (serial identifier 6d ff ff ff ff f0 00 8c 0e)
# Vendor Id CTL00f0, No Serial Number (-1), checksum 0x6D.
# Version 1.0, Vendor version 1.0
# ANSI string -->Creative ViBRA16X PnP<--

Make sure that IRQ5 is reserved for ISA-pnp devices.
(Enter BIOS setting to see.)

Describe the following in /etc/modprobe.d/sound .
```
options snd-sb16 isapnp=0 port=0x220 irq=5 dma8=1 dma16=5
```

Then execute 'sudu update-modules', and 'sudo modprobe snd-sb16'.

---

### Post by chageman on 2006-02-10
Hi again Far East
Have created the sound file and updated the modules as outlined
tried testing some of the sounds and unable to hear - made sure the volume was not muted and removed the speaker from the upper task bar
tried playing a CD with sound juicer and get "error playing CD. Reason:  Could not open resource for writing"
does this indicate that some sort of temp file needs to be created in order to play the CD?

also in the case of the system with the motherboard audio chip set (outlined in original email thread) 

dch@Zeus:~$ lspci -v | grep audio
0000:01:08.0 Multimedia audio controller: Rockwell International Riptide PCI Aud io Controller
dch@Zeus:~$

what are the contents of the sound file and what are the same final 2 commands then executed for the onboard (not ISA) device

Again thank you for your assistance as this newbie struggles forward!  Much appreciated

Best regards
cal

---

### Post by FarEast on 2006-02-10
I thought you wanted to use ViBRA for the time being, right?
For I am not a native speaker of English, I sometimes misunderstand what
others are saying:) .

Anyway... please read the following to understand what I am suggesting
you to solve your problem.

The command 'pnpdump' which belongs to the package 'isapnptools' helps
us to find devices on ISA bus.

Sound chips on ISA bus are not configured automatically like ones on PCI
bus.  So we have to load modules for them manually.  Also, they need
options including infomation of I/O port address, IRQ number, etc.

Visit the link below to know options required by 'snd-sb16'(for ViBRA).
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Vibra16X.&chip=sb16&module=sb16](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Vibra16X.&chip=sb16&module=sb16)

I usually look for success stories including the option values:) . 

For Debian-like distros including Ubuntu, the options have to be described
in the file /etc/modprobe.d/sound and they come into effect by executing
'sudo update-modules'.

---

