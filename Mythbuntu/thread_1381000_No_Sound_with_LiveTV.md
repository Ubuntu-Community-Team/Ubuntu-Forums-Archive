---
title: "No Sound with LiveTV"
date: 2010-01-14
forum: Mythbuntu
---

### Post by platticus on 2010-01-14
I've been a Ubuntu user for almost a year now and absolutely love it. I recently rebuilt my media center PC with Mythbuntu after thoroughly reading all about it, but I'm having an issue with the sound when using the LiveTV. First, here's the specs on the setup:

**The Computer**: 
HP Media Center m7060n
Pentium 4 3.0 Ghz
4.0 GB RAM
Detailed specs [[COLOR="Blue"]here[/COLOR]]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00306958&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN")

**The Display**:
Vizio 37" SV370XVT
Detailed specs [[COLOR="#0000ff"]here[/COLOR]]("http://www.vizio.com/sv370xvt.html#support")

**The Remote**: StreamZap PC Remote 

**The Operating System**: Mythbuntu 9.04
[INDENT]Note: I originally installed Mythbuntu 9.10, however due to the green fuzzy screen on the cable and improper remote integration, I reverted to 9.04, which fixed these things flawlessly.[/INDENT]

**What Works**:
Everything works flawlessly on my Mythbuntu distribution, except for the sound in the LiveTV, which I will get to next. The LiveTV does display, the channel guide does load (as does the mythfilldatabase function it uses), the GUI components of Mythbuntu (both frontend and backend work just fine), and the remote works perfectly.

**The Problem**:
[INDENT]Please be aware, although I am relatively saavy with Ubuntu (and learning more everyday), I'm still quite new to Mythbuntu distributions. So please bare with me for being a noob.[/INDENT]

The problem I seem to have is that the sound does not work when viewing (and presumably recording LiveTV). To complicate matters, the sounds DOES work in everything except LiveTV. I was able to get sound while playing a CD, a video file stored on the drive, etc. So, I know the setup is fine, the TV works great for sound and display.

**The Solution?**
I've not been able to find any information that was useful for fixing this problem. So if anyone can point me in the direction of such information or help me directly, I would be infinitely grateful.

Cheers

---

### Post by azmyth on 2010-01-14
What does the frontend log say when you start livetv? Can you hear sound on recorded shows? Can you hear sound in mythmusic or video or dvd?

---

### Post by platticus on 2010-01-14
Thank you for the quick reply!

Please pardon my ignorance, but how do I view the log? I will post it as soon as I know how.

The audio does work when playing a music CD, and a video file not from another source. I have not yet tried to record anything, so I do not know for certain that the sound does or does not work for recording. 

Hope this helps

---

### Post by azmyth on 2010-01-14
There's an option to view logs under one of the settings. I now compile so I can't remember exactly where it is. What I usually do is exit out of the frontend and open a terminal and start the frontend by issuing mythfrontend and it'll display the output in the terminal window. Start liveTV exit out and look at what it says in the terminal. Should give you a hint as to the problem.

---

### Post by platticus on 2010-01-15
Thank you again.

I did exactly as you instructed and here's the terminal output:
[INDENT]2010-01-15 09:35:07.307 Using runtime prefix = /usr
2010-01-15 09:35:07.832 XScreenSaver support enabled
2010-01-15 09:35:07.833 DPMS is active.
2010-01-15 09:35:07.833 Empty LocalHostName.
2010-01-15 09:35:07.834 Using localhost value of platticus-mythtop
2010-01-15 09:35:07.842 New DB connection, total: 1
2010-01-15 09:35:07.846 Connected to database 'mythconverg' at host: localhost
2010-01-15 09:35:07.847 Closing DB connection named 'DBManager0'
2010-01-15 09:35:07.850 Primary screen 0.
2010-01-15 09:35:07.850 Connected to database 'mythconverg' at host: localhost
2010-01-15 09:35:07.851 Using screen 0, 1920x1080 at 0,0
2010-01-15 09:35:07.858 New DB connection, total: 2
2010-01-15 09:35:07.858 Connected to database 'mythconverg' at host: localhost
2010-01-15 09:35:07.860 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2010-01-15 09:35:07.861 Enabled verbose msgs:  important general
2010-01-15 09:35:08.284 No theme dir: /home/platticus/.mythtv/themes/Mythbuntu-8.04
2010-01-15 09:35:08.287 Primary screen 0.
2010-01-15 09:35:08.288 Using screen 0, 1920x1080 at 0,0
2010-01-15 09:35:08.288 No theme dir: /home/platticus/.mythtv/themes/Mythbuntu-8.04
2010-01-15 09:35:08.288 Switching to square mode (Mythbuntu-8.04)
get fences failed: -1
param: 6, val: 0
2010-01-15 09:35:08.320 Using the Qt painter
2010-01-15 09:35:08.321 JoystickMenuClient Error: Joystick disabled - Failed to read /home/platticus/.mythtv/joystickmenurc
2010-01-15 09:35:08.322 lirc init success using configuration file: /home/platticus/.mythtv/lircrc
2010-01-15 09:35:09.414 Specified base font 'medium' does not exist for font clock
2010-01-15 09:35:09.414 Specified base font 'medium' does not exist for font small
2010-01-15 09:35:09.414 Specified base font 'medium' does not exist for font medium
2010-01-15 09:35:09.414 Specified base font 'medium' does not exist for font large
2010-01-15 09:35:09.415 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2010-01-15 09:35:09.587 Loading from: /usr/share/mythtv/themes/default/base.xml
2010-01-15 09:35:09.625 Registering Internal as a media playback plugin.
2010-01-15 09:35:09.800 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-01-15 09:35:09.836 Failed to run 'cdrecord --scanbus'
2010-01-15 09:35:09.843 Failed to run 'cdrecord --scanbus -dev=ATA'
2010-01-15 09:35:09.849 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2010-01-15 09:35:09.879 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2010-01-15 09:35:09.932 No theme dir: /home/platticus/.mythtv/themes/Mythbuntu-8.04
2010-01-15 09:35:15.494 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2010-01-15 09:35:15.495 Using protocol version 40
2010-01-15 09:35:15.508 TV: Attempting to change from None to WatchingLiveTV
2010-01-15 09:35:15.509 Using protocol version 40
2010-01-15 09:35:16.713 New DB connection, total: 3
2010-01-15 09:35:16.713 Connected to database 'mythconverg' at host: localhost
2010-01-15 09:35:16.726 DPMS Deactivated 
2010-01-15 09:35:16.793 Opening audio device 'default'. ch 2(2) sr 44100
2010-01-15 09:35:16.793 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2010-01-15 09:35:16.845 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
get fences failed: -1
param: 6, val: 0
2010-01-15 09:35:16.916 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2010-01-15 09:35:16.952 OSD Theme Dimensions W: 640 H: 480
2010-01-15 09:35:17.343 TV: Changing from None to WatchingLiveTV
2010-01-15 09:35:17.347 Realtime priority would require SUID as root.
2010-01-15 09:35:17.361 Video sync method can't support double framerate (refresh rate too low for bob deint)
2010-01-15 09:35:17.378 Video timing method: DRM
2010-01-15 09:35:29.560 TV: Attempting to change from WatchingLiveTV to None
2010-01-15 09:35:29.900 TV: Changing from WatchingLiveTV to None
2010-01-15 09:35:29.959 DPMS Reactivated.
2010-01-15 09:35:32.186 Deleting UPnP client...[/INDENT]

The following section is the concerning one for me:
[INDENT]2010-01-15 09:35:16.793 Opening audio device 'default'. ch 2(2) sr 44100
2010-01-15 09:35:16.793 Opening ALSA audio device 'default'.
ALSA lib control.c:909snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2010-01-15 09:35:16.845 AudioOutput Warning: Mixer attach error -2: No such file or directory
Check Mixer Name in Setup: '/dev/mixer'
get fences failed: -1
param: 6, val: 0[/INDENT]
However, I'm exactly sure what it means, or how to fix it.

---

### Post by azmyth on 2010-01-16
Go to:

Utilities/Setup -> Setup -> General -> screen 5

Mixer Device: /dev/mixer

Then change mixer device to **default** all lower case. Then try again. You may have to type default in as it may not be one of the choices.

Then try livetv again

---

### Post by platticus on 2010-01-16
I altered the setting as you recommend, and unfortunately, sound with LiveTV still does not work. I attached a screenshot of the settings screen you instructed me to modify. Is there anything else that looks as though it needs modifying?

---

### Post by azmyth on 2010-01-16
hmm, looks good. What kind of TV card are you using. Does it need a loop back cable?

---

### Post by platticus on 2010-01-16
The capture card is listed (in Mythbuntu) as an Asus PVR-416 [cx8800]. As a side note, when this machine ran Windows XP Media Center Edition (as it was stock from HP), I seem to remember something about Connexant(sp?), not sure if that was a driver or some sort of manufacturer or what.

As to your question about a loopback cable, I am unaware of what a loopback cable is, what it does or if this PC needs one to use sound. 

Additionally, I have attached a screenshot of the capture card setup, hope it helps.

---

### Post by azmyth on 2010-01-16
Loopback cables were needed to get the sound from the tv tuner card to the PC. For example, I use a ATI TV Wonder as a backup and this card needs one. You only need this if the card doesn't decode on the tuner card. You shouldn't need the cable.

From looking at the wiki, it looks like some work is needed to get the audio part of the card working since the blackbird module is the audio part.

[http://www.mythtv.org/wiki/AVerMedia_M150-D](http://www.mythtv.org/wiki/AVerMedia_M150-D)

I'd do a 

$locate blackbird-fw-enc.bin 
then
$locate v4l-cx2341x-enc.fw

If both of these come up empty, then I'd follow the directions in the wiki.

---

### Post by platticus on 2010-01-18
That wiki is quite a fantastic one, thank you for the information. Unfortunately, the sound still does not work. Here's what I've done so far:

As far as the locate calls, here's the output:
[INDENT]**platticus@platticus-mythtop:~$ locate blackbird-fw-enc.bin**
**platticus@platticus-mythtop:~$ locate v4l-cx2341x-enc.fw**
/lib/firmware/v4l-cx2341x-enc.fw
[/INDENT]
After reading through the wiki, I decided it was worth a shot to follow the instructions to install the blackbird-fw-enc.bin driver. After doing so, the same result ensued.

Following this, I attempted the instructions in the wiki regarding Video4Linux muting options: 
[INDENT]v4lctl -c /dev/video1 volume mute off
and
v4l2-ctl -d /dev/video1 -c mute=0[/INDENT]
And the sound still does not work with LiveTV.

Following this, I attempted the mplayer tv capture, which produced the following log: 
[INDENT]MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: ASUS PVR-416
 Tuner cap:
 Tuner rxs:
 Capabilites:  video capture  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = NTSC-M; 1 = NTSC-M-JP; 2 = NTSC-443; 3 = PAL-BG; 4 = PAL-I; 5 = PAL-DK; 6 = PAL-M; 7 = PAL-N; 8 = PAL-Nc; 9 = PAL-60; 10 = SECAM-DK; 11 = SECAM-L;
 inputs: 0 = Television; 1 = S-Video;
 Current input: 0
 Current format: BGR24
v4l2: current audio mode is : MONO
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed UYVY)
VDec: using Packed UYVY as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Packed UYVY 
Selected video codec: [rawuyvy] vfm: raw (RAW UYVY)
==========================================================================
Audio: no sound
Starting playback...
v4l2: 877 frames successfully processed, 0 frames dropped.
[/INDENT]

As it says, no sound. But the TV worked flawlessly.

Following this, I attempted the verification of driver installation, as instructed by the wiki:

[INDENT]**platticus@platticus-mythtop:~$ lsmod | grep blackbird**
cx88_blackbird         28036  0 
cx2341x                22148  1 cx88_blackbird
cx8802                 27012  1 cx88_blackbird
cx8800                 45036  1 cx88_blackbird
cx88xx                 88104  3 cx88_blackbird,cx8802,cx8800
videodev               45184  5 cx88_blackbird,tuner,cx8800,cx88xx,compat_ioctl32
v4l2_common            23296  4 cx88_blackbird,cx2341x,tuner,cx8800
videobuf_dma_sg        22660  4 cx88_blackbird,cx8802,cx8800,cx88xx
videobuf_core          29828  6 cx88_blackbird,cx8802,cx8800,cx88xx,videobuf_dvb,videobuf_dma_sg
[/INDENT]

[INDENT]**platticus@platticus-mythtop:~$ dmesg**
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-17-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009 (Ubuntu 2.6.28-17.58-generic)
[    0.000000] Command line: root=UUID=e129db9e-847c-458d-b375-e15bf1d15b1f ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000c77c0000 (usable)
[    0.000000]  BIOS-e820: 00000000c77c0000 - 00000000c77ce000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000c77ce000 - 00000000c77f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000c77f0000 - 00000000c7800000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xc77c0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000c77c0000 (usable)
[    0.000000]  modified: 00000000c77c0000 - 00000000c77ce000 (ACPI data)
[    0.000000]  modified: 00000000c77ce000 - 00000000c77f0000 (ACPI NVS)
[    0.000000]  modified: 00000000c77f0000 - 00000000c7800000 (reserved)
[    0.000000]  modified: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-00000000c77c0000
[    0.000000]  0000000000 - 00c7600000 page 2M
[    0.000000]  00c7600000 - 00c77c0000 page 4k
[    0.000000] kernel direct mapping tables up to c77c0000 @ 10000-16000
[    0.000000] last_map_addr: c77c0000 end: c77c0000
[    0.000000] RAMDISK: 3784d000 - 37fefe49
[    0.000000] ACPI: RSDP 000FB560, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT C77C0000, 0034 (r1 A M I  OEMRSDT   1000623 MSFT       97)
[    0.000000] ACPI: FACP C77C0200, 0081 (r1 A M I  OEMFACP   1000623 MSFT       97)
[    0.000000] ACPI: DSDT C77C0400, 47BE (r1  A0005 A0005102      102 INTL  2002026)
[    0.000000] ACPI: FACS C77CE000, 0040
[    0.000000] ACPI: APIC C77C0390, 0070 (r1 A M I  OEMAPIC   1000623 MSFT       97)
[    0.000000] ACPI: OEMB C77CE040, 0060 (r1 A M I  AMI_OEM   1000623 MSFT       97)
[    0.000000] ACPI: MCFG C77C4BC0, 003C (r1 A M I  OEMMCFG   1000623 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 00c77c0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b7cbb0]    TEXT DATA BSS ==> [0000200000 - 0000b7cbb0]
[    0.000000]   #3 [003784d000 - 0037fefe49]          RAMDISK ==> [003784d000 - 0037fefe49]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20002bfffff] PMD -> [ffff880001200000-ffff880003dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000c77c0
[    0.000000] On node 0 totalpages: 816975
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2533 pages reserved
[    0.000000]   DMA zone: 1394 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11116 pages used for memmap
[    0.000000]   DMA32 zone: 801876 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c8000000 (gap: c7800000:38380000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 803270
[    0.000000] Kernel command line: root=UUID=e129db9e-847c-458d-b375-e15bf1d15b1f ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3000.833 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] allocated 32768000 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 3166112k/3268352k available (4750k kernel code, 452k absent, 101072k reserved, 2523k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 6001.66 BogoMIPS (lpj=12003332)
[    0.004037] Security Framework initialized
[    0.004044] SELinux:  Disabled at boot.
[    0.004062] AppArmor: AppArmor initialized
[    0.004073] Mount-cache hash table entries: 256
[    0.004235] Initializing cgroup subsys ns
[    0.004239] Initializing cgroup subsys cpuacct
[    0.004242] Initializing cgroup subsys memory
[    0.004247] Initializing cgroup subsys freezer
[    0.004267] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004270] CPU: L2 cache: 2048K
[    0.004273] CPU: Physical Processor ID: 0
[    0.004275] CPU: Processor Core ID: 0
[    0.004279] using mwait in idle threads.
[    0.007123] ACPI: Core revision 20080926
[    0.009792] ACPI: Checking initramfs for custom DSDT
[    0.336061] Setting APIC routing to flat
[    0.336488] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.379555] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[    0.380001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6002.11 BogoMIPS (lpj=12004225)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.464557] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[    0.464609] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.468058] Brought up 2 CPUs
[    0.468062] Total of 2 processors activated (12003.77 BogoMIPS).
[    0.468111] CPU0 attaching sched-domain:
[    0.468114]  domain 0: span 0-1 level SIBLING
[    0.468117]   groups: 0 1
[    0.468125] CPU1 attaching sched-domain:
[    0.468127]  domain 0: span 0-1 level SIBLING
[    0.468129]   groups: 1 0
[    0.468225] net_namespace: 1400 bytes
[    0.468230] Booting paravirtualized kernel on bare hardware
[    0.468389] Time: 15:14:29  Date: 01/18/10
[    0.468389] regulator: core version 0.5
[    0.468389] NET: Registered protocol family 16
[    0.468389] ACPI: bus type pci registered
[    0.468389] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.468389] PCI: Not using MMCONFIG.
[    0.468389] PCI: Using configuration type 1 for base access
[    0.469221] ACPI: EC: Look up EC in DSDT
[    0.481647] ACPI: Interpreter enabled
[    0.481651] ACPI: (supports S0 S1 S3 S4 S5)
[    0.481681] ACPI: Using IOAPIC for interrupt routing
[    0.481759] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.487555] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.501127] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.508841] ACPI: No dock devices found.
[    0.508916] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.509015] pci 0000:00:02.0: reg 10 32bit mmio: [0xccf80000-0xccffffff]
[    0.509022] pci 0000:00:02.0: reg 14 io port: [0xb800-0xb807]
[    0.509027] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.509032] pci 0000:00:02.0: reg 1c 32bit mmio: [0xccf40000-0xccf7ffff]
[    0.509109] pci 0000:00:1b.0: reg 10 64bit mmio: [0xccf38000-0xccf3bfff]
[    0.509140] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.509144] pci 0000:00:1b.0: PME# disabled
[    0.509192] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.509196] pci 0000:00:1c.0: PME# disabled
[    0.509248] pci 0000:00:1d.0: reg 20 io port: [0xa400-0xa41f]
[    0.509297] pci 0000:00:1d.1: reg 20 io port: [0xa800-0xa81f]
[    0.509347] pci 0000:00:1d.2: reg 20 io port: [0xb000-0xb01f]
[    0.509395] pci 0000:00:1d.3: reg 20 io port: [0xb400-0xb41f]
[    0.509449] pci 0000:00:1d.7: reg 10 32bit mmio: [0xccf37c00-0xccf37fff]
[    0.509489] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.509494] pci 0000:00:1d.7: PME# disabled
[    0.509604] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.509610] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.509614] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.509636] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.509643] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.509650] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.509656] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.509663] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.509703] pci 0000:00:1f.2: reg 10 io port: [0xa000-0xa007]
[    0.509709] pci 0000:00:1f.2: reg 14 io port: [0x9800-0x9803]
[    0.509715] pci 0000:00:1f.2: reg 18 io port: [0x9400-0x9407]
[    0.509722] pci 0000:00:1f.2: reg 1c io port: [0x9000-0x9003]
[    0.509728] pci 0000:00:1f.2: reg 20 io port: [0x8800-0x880f]
[    0.509745] pci 0000:00:1f.2: PME# supported from D3hot
[    0.509749] pci 0000:00:1f.2: PME# disabled
[    0.509795] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.509858] pci 0000:00:1c.0: bridge io port: [0xc000-0xcfff]
[    0.509904] pci 0000:02:01.0: reg 10 32bit mmio: [0xcffff800-0xcfffffff]
[    0.509911] pci 0000:02:01.0: reg 14 io port: [0xe800-0xe87f]
[    0.509948] pci 0000:02:01.0: supports D2
[    0.509950] pci 0000:02:01.0: PME# supported from D2 D3hot D3cold
[    0.509955] pci 0000:02:01.0: PME# disabled
[    0.509991] pci 0000:02:02.0: reg 10 io port: [0xe400-0xe4ff]
[    0.509998] pci 0000:02:02.0: reg 14 32bit mmio: [0xcffff400-0xcffff4ff]
[    0.510034] pci 0000:02:02.0: supports D1 D2
[    0.510036] pci 0000:02:02.0: PME# supported from D1 D2 D3hot D3cold
[    0.510041] pci 0000:02:02.0: PME# disabled
[    0.510085] pci 0000:02:04.0: reg 10 32bit mmio: [0xcd000000-0xcdffffff]
[    0.510162] pci 0000:02:04.2: reg 10 32bit mmio: [0xce000000-0xceffffff]
[    0.510244] pci 0000:02:05.0: reg 10 32bit mmio: [0xcffff000-0xcffff0ff]
[    0.510252] pci 0000:02:05.0: reg 14 io port: [0xe000-0xe007]
[    0.510259] pci 0000:02:05.0: reg 18 io port: [0xd800-0xd8ff]
[    0.510290] pci 0000:02:05.0: supports D2
[    0.510292] pci 0000:02:05.0: PME# supported from D2 D3hot D3cold
[    0.510297] pci 0000:02:05.0: PME# disabled
[    0.510338] pci 0000:00:1e.0: transparent bridge
[    0.510343] pci 0000:00:1e.0: bridge io port: [0xd000-0xefff]
[    0.510347] pci 0000:00:1e.0: bridge 32bit mmio: [0xcd000000-0xcfffffff]
[    0.510363] bus 00 -> node 0
[    0.510372] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.510651] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.513607] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.513778] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.513947] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.514113] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.514281] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.514449] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.514616] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.514784] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.514945] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - A9, should be A5 [20080926]
[    0.514975] ACPI: WMI: Mapper loaded
[    0.515043] SCSI subsystem initialized
[    0.515043] libata version 3.00 loaded.
[    0.515043] usbcore: registered new interface driver usbfs
[    0.515043] usbcore: registered new interface driver hub
[    0.515043] usbcore: registered new device driver usb
[    0.515043] PCI: Using ACPI for IRQ routing
[    0.528014] Bluetooth: Core ver 2.13
[    0.528033] NET: Registered protocol family 31
[    0.528033] Bluetooth: HCI device and connection manager initialized
[    0.528033] Bluetooth: HCI socket layer initialized
[    0.528033] NET: Registered protocol family 8
[    0.528033] NET: Registered protocol family 20
[    0.528049] NetLabel: Initializing
[    0.528052] NetLabel:  domain hash size = 128
[    0.528054] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.528072] NetLabel:  unlabeled traffic allowed by default
[    0.528185] hpet clockevent registered
[    0.528188] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.528193] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.528199] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.532079] AppArmor: AppArmor Filesystem Enabled
[    0.544015] pnp: PnP ACPI init
[    0.544026] ACPI: bus type pnp registered
[    0.549173] pnp: PnP ACPI: found 15 devices
[    0.549176] ACPI: ACPI bus type pnp unregistered
[    0.549190] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.549200] system 00:07: ioport range 0x680-0x6ff has been reserved
[    0.549207] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.549210] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.549212] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.549216] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.549218] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.549226] system 00:0a: iomem range 0xffc00000-0xfff7ffff has been reserved
[    0.549234] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.549238] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.549245] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.549254] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.549262] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.549265] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.549268] system 00:0e: iomem range 0x100000-0xc77fffff could not be reserved
[    0.554000] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.554004] pci 0000:00:1c.0:   IO window: 0xc000-0xcfff
[    0.554010] pci 0000:00:1c.0:   MEM window: disabled
[    0.554014] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.554021] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.554024] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.554029] pci 0000:00:1e.0:   MEM window: 0xcd000000-0xcfffffff
[    0.554033] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.554049] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.554056] pci 0000:00:1c.0: setting latency timer to 64
[    0.554064] pci 0000:00:1e.0: setting latency timer to 64
[    0.554070] bus: 00 index 0 io port: [0x00-0xffff]
[    0.554073] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.554076] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.554078] bus: 01 index 1 mmio: [0x0-0x0]
[    0.554080] bus: 01 index 2 mmio: [0x0-0x0]
[    0.554082] bus: 01 index 3 mmio: [0x0-0x0]
[    0.554084] bus: 02 index 0 io port: [0xd000-0xefff]
[    0.554086] bus: 02 index 1 mmio: [0xcd000000-0xcfffffff]
[    0.554088] bus: 02 index 2 mmio: [0x0-0x0]
[    0.554090] bus: 02 index 3 io port: [0x00-0xffff]
[    0.554092] bus: 02 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.554104] NET: Registered protocol family 2
[    0.588072] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.588760] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.590812] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.591420] TCP: Hash tables configured (established 262144 bind 65536)
[    0.591423] TCP reno registered
[    0.600123] NET: Registered protocol family 1
[    0.600288] checking if image is initramfs... it is
[    1.028701] Switched to high resolution mode on CPU 1
[    1.032037] Switched to high resolution mode on CPU 0
[    1.261259] Freeing initrd memory: 7819k freed
[    1.266042] audit: initializing netlink socket (disabled)
[    1.266065] type=2000 audit(1263827669.265:1): initialized
[    1.273399] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.274844] VFS: Disk quotas dquot_6.5.1
[    1.274912] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.275614] fuse init (API version 7.10)
[    1.275709] msgmni has been set to 6200
[    1.275919] alg: No test for stdrng (krng)
[    1.275941] io scheduler noop registered
[    1.275943] io scheduler anticipatory registered
[    1.275945] io scheduler deadline registered
[    1.275994] io scheduler cfq registered (default)
[    1.276012] pci 0000:00:02.0: Boot video device
[    1.280349] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.280386] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.280416] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.280429] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.280447] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.280465] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.280537] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.280737] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.280899] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.280903] ACPI: Power Button (FF) [PWRF]
[    1.280963] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.280966] ACPI: Power Button (CM) [PWRB]
[    1.281531] ACPI: SSDT C77C4C00, 02FC (r1    AMI   CPU1PM        1 INTL  2002026)
[    1.281865] processor ACPI_CPU:00: registered as cooling_device0
[    1.281870] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.282132] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] - C9, should be CF [20080926]
[    1.282139] ACPI: SSDT C77C4F00, 02FC (r1    AMI   CPU2PM        1 INTL  2002026)
[    1.282425] processor ACPI_CPU:01: registered as cooling_device1
[    1.316140] Linux agpgart interface v0.103
[    1.316152] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.317327] brd: module loaded
[    1.317699] loop: module loaded
[    1.317791] Fixed MDIO Bus: probed
[    1.317798] PPP generic driver version 2.4.2
[    1.317865] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.317896] Driver 'sd' needs updating - please use bus_type methods
[    1.317911] Driver 'sr' needs updating - please use bus_type methods
[    1.317988] ata_piix 0000:00:1f.1: version 2.12
[    1.318004] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.318046] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.318143] scsi0 : ata_piix
[    1.318252] scsi1 : ata_piix
[    1.320955] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.320959] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.660743] ata1.00: ATAPI: HP  DVD Writer 640, CS30, max UDMA/33
[    1.660769] ata1.01: ATAPI: LTN486S, YQSK, max PIO4
[    1.679548] ata1.00: configured for UDMA/33
[    1.684282] ata1.01: configured for PIO4
[    1.850867] isa bounce pool size: 16 pages
[    1.856254] scsi 0:0:0:0: CD-ROM            HP       DVD Writer 640c  CS30 PQ: 0 ANSI: 5
[    1.860159] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.860162] Uniform CD-ROM driver Revision: 3.20
[    1.860263] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.860312] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.860609] scsi 0:0:1:0: CD-ROM            COMPAQ   CD-ROM LTN486S   YQSK PQ: 0 ANSI: 5
[    1.863432] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.863504] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    1.863549] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.863577] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.863582] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.863624] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.863708] scsi2 : ata_piix
[    1.863789] scsi3 : ata_piix
[    1.863834] ata3: SATA max UDMA/133 cmd 0xa000 ctl 0x9800 bmdma 0x8800 irq 19
[    1.863838] ata4: SATA max UDMA/133 cmd 0x9400 ctl 0x9000 bmdma 0x8808 irq 19
[    2.025514] ata3.00: ATA-6: WDC WD2000JD-22HBB0, 08.02D08, max UDMA/133
[    2.025518] ata3.00: 390721968 sectors, multi 16: LBA48 
[    2.041511] ata3.00: configured for UDMA/133
[    2.206844] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2000JD-22H 08.0 PQ: 0 ANSI: 5
[    2.206954] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    2.206977] sd 2:0:0:0: [sda] Write Protect is off
[    2.206981] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.207018] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.207092] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    2.207113] sd 2:0:0:0: [sda] Write Protect is off
[    2.207116] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.207152] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.207157]  sda: sda1 sda2 < sda5 sda6 >
[    2.250855] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.250903] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.251617] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.251643] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.251667] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.251672] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.251740] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.255639] ehci_hcd 0000:00:1d.7: debug port 1
[    2.255646] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.255659] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xccf37c00
[    2.268010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.268094] usb usb1: configuration #1 chosen from 1 choice
[    2.268126] hub 1-0:1.0: USB hub found
[    2.268136] hub 1-0:1.0: 8 ports detected
[    2.268265] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.268282] uhci_hcd: USB Universal Host Controller Interface driver
[    2.268316] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.268323] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.268327] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.268378] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.268402] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a400
[    2.268483] usb usb2: configuration #1 chosen from 1 choice
[    2.268514] hub 2-0:1.0: USB hub found
[    2.268523] hub 2-0:1.0: 2 ports detected
[    2.268617] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.268623] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.268627] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.268680] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.268704] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a800
[    2.268787] usb usb3: configuration #1 chosen from 1 choice
[    2.268819] hub 3-0:1.0: USB hub found
[    2.268827] hub 3-0:1.0: 2 ports detected
[    2.268920] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.268931] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.268935] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.268986] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.269019] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b000
[    2.269112] usb usb4: configuration #1 chosen from 1 choice
[    2.269141] hub 4-0:1.0: USB hub found
[    2.269148] hub 4-0:1.0: 2 ports detected
[    2.269243] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.269250] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.269254] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.269304] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.269337] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b400
[    2.269421] usb usb5: configuration #1 chosen from 1 choice
[    2.269450] hub 5-0:1.0: USB hub found
[    2.269458] hub 5-0:1.0: 2 ports detected
[    2.269626] PNP: No PS/2 controller found. Probing ports directly.
[    2.272297] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.272304] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.284049] mice: PS/2 mouse device common for all mice
[    2.320080] rtc_cmos 00:03: RTC can wake from S4
[    2.320121] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.320150] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    2.320230] device-mapper: uevent: version 1.0.3
[    2.320347] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.320462] device-mapper: multipath: version 1.0.5 loaded
[    2.320467] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.320593] cpuidle: using governor ladder
[    2.320597] cpuidle: using governor menu
[    2.321090] TCP cubic registered
[    2.321178] NET: Registered protocol family 10
[    2.321631] lo: Disabled Privacy Extensions
[    2.321967] NET: Registered protocol family 17
[    2.321990] Bluetooth: L2CAP ver 2.11
[    2.321992] Bluetooth: L2CAP socket layer initialized
[    2.321995] Bluetooth: SCO (Voice Link) ver 0.6
[    2.321997] Bluetooth: SCO socket layer initialized
[    2.322035] Bluetooth: RFCOMM socket layer initialized
[    2.322048] Bluetooth: RFCOMM TTY layer initialized
[    2.322051] Bluetooth: RFCOMM ver 1.10
[    2.322969] registered taskstats version 1
[    2.323091]   Magic number: 10:80:235
[    2.323171] rtc_cmos 00:03: setting system clock to 2010-01-18 15:14:31 UTC (1263827671)
[    2.323175] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.323178] EDD information not available.
[    2.323220] Freeing unused kernel memory: 536k freed
[    2.323498] Write protecting the kernel read-only data: 6688k
[    2.635621] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.635661] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.639596] 8139too Fast Ethernet driver 0.9.28
[    2.639651] 8139too 0000:02:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.641106] eth0: RealTek RTL8139 at 0xe400, 00:11:d8:ab:36:0e, IRQ 21
[    2.641110] eth0:  Identified 8139 chip type 'RTL-8101'
[    2.644614] ohci1394 0000:02:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.697475] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[cffff800-cfffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.941038] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.118556] usb 2-1: configuration #1 chosen from 1 choice
[    3.166042] PM: Starting manual resume from disk
[    3.166047] PM: Resume from partition 8:5
[    3.166049] PM: Checking hibernation image.
[    3.166189] PM: Resume from disk failed.
[    3.208033] kjournald starting.  Commit interval 5 seconds
[    3.208051] EXT3-fs: mounted filesystem with ordered data mode.
[    3.368019] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    3.541508] usb 5-1: configuration #1 chosen from 1 choice
[    4.012177] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800001bd5c7]
[    4.629855] udev: starting version 141
[    5.026422] agpgart-intel 0000:00:00.0: Intel 915G Chipset
[    5.027214] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    5.030718] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    5.037398] end_request: I/O error, dev sr0, sector 0
[    5.037410] Buffer I/O error on device sr0, logical block 0
[    5.037424] Buffer I/O error on device sr0, logical block 1
[    5.037432] Buffer I/O error on device sr0, logical block 2
[    5.037438] Buffer I/O error on device sr0, logical block 3
[    5.042722] end_request: I/O error, dev sr0, sector 0
[    5.042735] Buffer I/O error on device sr0, logical block 0
[    5.058921] parport_pc 00:06: reported by Plug and Play ACPI
[    5.058987] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    5.177055] Initializing USB Mass Storage driver...
[    5.178104] scsi4 : SCSI emulation for USB Mass Storage devices
[    5.178356] usb-storage: device found at 2
[    5.178359] usb-storage: waiting for device to settle before scanning
[    5.178381] usbcore: registered new interface driver usb-storage
[    5.178429] USB Mass Storage support registered.
[    5.194487] intel_rng: FWH not detected
[    5.217388] lirc_dev: IR Remote Control driver registered, major 61 
[    5.320779] input: PC Speaker as /devices/platform/pcspkr/input/input3
[    5.521741] Linux video capture interface: v2.00
[    5.748459] ppdev: user-space parallel port driver
[    5.789536] lirc_streamzap[-1]: Streamzap, Inc. Streamzap Remote Control on usb2:2 attached
[    5.789540] lirc_dev: lirc_register_plugin: sample_rate: 0
[    5.789755] usbcore: registered new interface driver lirc_streamzap
[    5.789788] lirc_streamzap $Revision: 1.27 $ registered
[    5.922538] iTCO_vendor_support: vendor-support=0
[    5.940263] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    5.940550] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
[    5.940698] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    6.061336] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[    6.061822] cx8800 0000:02:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.062844] cx88[0]: subsystem: 1043:4823, board: ASUS PVR-416 [card=12,autodetected], frontend(s): 0
[    6.062847] cx88[0]: TV tuner type 43, Radio tuner type -1
[    6.072735] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[    6.298443] tuner' 0-0043: chip found @ 0x86 (cx88[0])
[    6.311290] tda9887 0-0043: creating new instance
[    6.311297] tda9887 0-0043: tda988[5/6/7] found
[    6.336853] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.336950] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.339747] All bytes are equal. It is not a TEA5767
[    6.339827] tuner' 0-0060: chip found @ 0xc0 (cx88[0])
[    6.389517] tuner-simple 0-0060: creating new instance
[    6.389522] tuner-simple 0-0060: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[    6.391882] cx88[0]/0: found at 0000:02:04.0, rev: 5, irq: 16, latency: 64, mmio: 0xcd000000
[    6.391976] cx88[0]/0: registered device video0 [v4l2]
[    6.392022] cx88[0]/0: registered device vbi0
[    6.392062] cx88[0]/0: registered device radio0
[    6.393515] cx88[0]/2: cx2388x 8802 Driver Manager
[    6.393533] cx88-mpeg driver manager 0000:02:04.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.393547] cx88[0]/2: found at 0000:02:04.2, rev: 5, irq: 16, latency: 64, mmio: 0xce000000
[    6.424868] cx2388x blackbird driver version 0.0.6 loaded
[    6.424876] cx88/2: registering cx8802 driver, type: blackbird access: shared
[    6.424882] cx88[0]/2: subsystem: 1043:4823, board: ASUS PVR-416 [card=12]
[    6.424887] cx88[0]/2: cx23416 based mpeg encoder (blackbird reference design)
[    6.425113] cx88[0]/2-bb: Firmware and/or mailbox pointer not initialized or corrupted
[    6.432062] cx88-mpeg driver manager 0000:02:04.2: firmware: requesting v4l-cx2341x-enc.fw
[    6.595654] lp0: using parport0 (interrupt-driven).
[    7.262805] Adding 995988k swap on /dev/sda5.  Priority:-1 extents:1 across:995988k
[    8.030116] EXT3 FS on sda1, internal journal
[    9.237566] cx88[0]/2-bb: Firmware upload successful.
[    9.250863] cx88[0]/2-bb: Firmware version is 0x02060039
[    9.258925] cx88[0]/2: registered device video1 [mpeg]
[    9.526485] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[    9.532470] SGI XFS Quota Management subsystem
[    9.576611] XFS mounting filesystem sda6
[    9.790788] Ending clean XFS mount for filesystem: sda6
[   10.178639] usb-storage: device scan complete
[   10.181612] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   10.184682] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   10.187615] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   10.190615] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   10.198485] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   10.198618] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   10.205814] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   10.205931] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   10.211796] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   10.211915] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   10.218375] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   10.218482] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   10.460569] type=1505 audit(1263827679.636:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2124
[   10.460715] type=1505 audit(1263827679.636:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2124
[   10.460761] type=1505 audit(1263827679.636:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2124
[   10.460810] type=1505 audit(1263827679.636:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2124
[   10.595818] type=1505 audit(1263827679.768:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2129
[   10.595992] type=1505 audit(1263827679.768:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2129
[   10.625479] type=1505 audit(1263827679.800:8): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2133
[   10.654418] type=1505 audit(1263827679.828:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2137
[   11.086891] RPC: Registered udp transport module.
[   11.086896] RPC: Registered tcp transport module.
[   11.197820] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   15.550808] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   15.580848] NFSD: starting 90-second grace period
[   21.606101] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.606106] Bluetooth: BNEP filters: protocol multicast
[   21.665824] Bridge firewalling registered
[   24.326576] [drm] Initialized drm 1.1.0 20060810
[   24.357747] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.357755] pci 0000:00:02.0: setting latency timer to 64
[   24.357833] [drm:i915_gem_detect_bit_6_swizzle] *ERROR* Couldn't read from MCHBAR.  Disabling tiling.
[   24.357932] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   24.361634] [drm:i915_setparam] *ERROR* unknown parameter 4
[   24.361682] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   25.108604] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   27.823989] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   38.348012] eth0: no IPv6 routers present
[   39.235392] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  821.706679] cx88[0]/2-bb: VIDIOC_G_FMT: w: 720, h: 480, f: 4
[  849.993643] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  851.156007] cx88[0]: video y / packed - dma channel status dump
[  851.156014] cx88[0]:   cmds: initial risc: 0x914fb000
[  851.156017] cx88[0]:   cmds: cdt base    : 0x00180440
[  851.156021] cx88[0]:   cmds: cdt size    : 0x0000000c
[  851.156024] cx88[0]:   cmds: iq base     : 0x00180400
[  851.156027] cx88[0]:   cmds: iq size     : 0x00000010
[  851.156030] cx88[0]:   cmds: risc pc     : 0x914ae014
[  851.156033] cx88[0]:   cmds: iq wr ptr   : 0x0000010c
[  851.156038] cx88[0]:   cmds: iq rd ptr   : 0x00000100
[  851.156041] cx88[0]:   cmds: cdt current : 0x00000478
[  851.156044] cx88[0]:   cmds: pci target  : 0x914f9e00
[  851.156047] cx88[0]:   cmds: line / byte : 0x028d0000
[  851.156051] cx88[0]:   risc0: 0x1c000300 [ write sol eol count=768 ]
[  851.156058] cx88[0]:   risc1: 0x914fa100 [ arg #1 ]
[  851.156062] cx88[0]:   risc2: 0x1c000300 [ write sol eol count=768 ]
[  851.156068] cx88[0]:   risc3: 0x914fa700 [ arg #1 ]
[  851.156072] cx88[0]:   iq 0: 0x1c000300 [ write sol eol count=768 ]
[  851.156079] cx88[0]:   iq 1: 0x914fa100 [ arg #1 ]
[  851.156082] cx88[0]:   iq 2: 0x1c000300 [ write sol eol count=768 ]
[  851.156088] cx88[0]:   iq 3: 0x914fa700 [ arg #1 ]
[  851.156091] cx88[0]:   iq 4: 0x1c000300 [ write sol eol count=768 ]
[  851.156098] cx88[0]:   iq 5: 0x914fad00 [ arg #1 ]
[  851.156101] cx88[0]:   iq 6: 0x71010000 [ jump irq1 cnt0 count=0 ]
[  851.156107] cx88[0]:   iq 7: 0x80008000 [ arg #1 ]
[  851.156110] cx88[0]:   iq 8: 0x1c000300 [ write sol eol count=768 ]
[  851.156117] cx88[0]:   iq 9: 0x91420000 [ arg #1 ]
[  851.156120] cx88[0]:   iq a: 0x1c000300 [ write sol eol count=768 ]
[  851.156126] cx88[0]:   iq b: 0x91420600 [ arg #1 ]
[  851.156129] cx88[0]:   iq c: 0x1c000300 [ write sol eol count=768 ]
[  851.156135] cx88[0]:   iq d: 0x914f9500 [ arg #1 ]
[  851.156138] cx88[0]:   iq e: 0x1c000300 [ write sol eol count=768 ]
[  851.156145] cx88[0]:   iq f: 0x914f9b00 [ arg #1 ]
[  851.156147] cx88[0]: fifo: 0x00180c00 -> 0x183400
[  851.156149] cx88[0]: ctrl: 0x00180400 -> 0x180460
[  851.156152] cx88[0]:   ptr1_reg: 0x00181800
[  851.156155] cx88[0]:   ptr2_reg: 0x00180488
[  851.156158] cx88[0]:   cnt1_reg: 0x00000009
[  851.156161] cx88[0]:   cnt2_reg: 0x00000000
[  851.156169] cx88[0]/0: [ffff8800ae1a5c00/0] timeout - dma=0x914fb000
[  851.156172] cx88[0]/0: [ffff8800ae1a5000/1] timeout - dma=0x914ae000
[  872.959770] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  881.783319] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 1316.390293] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 1325.524006] cx88[0]: video y / packed - dma channel status dump
[ 1325.524013] cx88[0]:   cmds: initial risc: 0xad82e000
[ 1325.524017] cx88[0]:   cmds: cdt base    : 0x00180440
[ 1325.524020] cx88[0]:   cmds: cdt size    : 0x0000000c
[ 1325.524023] cx88[0]:   cmds: iq base     : 0x00180400
[ 1325.524026] cx88[0]:   cmds: iq size     : 0x00000010
[ 1325.524030] cx88[0]:   cmds: risc pc     : 0xad82e034
[ 1325.524033] cx88[0]:   cmds: iq wr ptr   : 0x00000101
[ 1325.524036] cx88[0]:   cmds: iq rd ptr   : 0x00000105
[ 1325.524039] cx88[0]:   cmds: cdt current : 0x00000458
[ 1325.524042] cx88[0]:   cmds: pci target  : 0xbfc77000
[ 1325.524045] cx88[0]:   cmds: line / byte : 0x02900000
[ 1325.524048] cx88[0]:   risc0: 0x80008000 [ sync resync count=0 ]
[ 1325.524055] cx88[0]:   risc1: 0x1c000300 [ write sol eol count=768 ]
[ 1325.524061] cx88[0]:   risc2: 0xad94c000 [ arg #1 ]
[ 1325.524065] cx88[0]:   risc3: 0x1c000300 [ write sol eol count=768 ]
[ 1325.524071] cx88[0]:   iq 0: 0xb3d7de00 [ writerm irq2 irq1 23 22 20 18 cnt1 cnt0 resync 14 12 count=3584 ]
[ 1325.524085] cx88[0]:   iq 1: 0x1c000300 [ arg #1 ]
[ 1325.524088] cx88[0]:   iq 2: 0xbfc76d00 [ arg #2 ]
[ 1325.524091] cx88[0]:   iq 3: 0x71010000 [ jump irq1 cnt0 count=0 ]
[ 1325.524097] cx88[0]:   iq 4: 0x80008000 [ arg #1 ]
[ 1325.524100] cx88[0]:   iq 5: 0x1c000300 [ write sol eol count=768 ]
[ 1325.524107] cx88[0]:   iq 6: 0xad94c000 [ arg #1 ]
[ 1325.524110] cx88[0]:   iq 7: 0x1c000300 [ write sol eol count=768 ]
[ 1325.524116] cx88[0]:   iq 8: 0xad94c600 [ arg #1 ]
[ 1325.524119] cx88[0]:   iq 9: 0x1c000300 [ write sol eol count=768 ]
[ 1325.524125] cx88[0]:   iq a: 0xad94cc00 [ arg #1 ]
[ 1325.524128] cx88[0]:   iq b: 0x1c000300 [ write sol eol count=768 ]
[ 1325.524135] cx88[0]:   iq c: 0xb3d7d200 [ arg #1 ]
[ 1325.524138] cx88[0]:   iq d: 0x1c000300 [ write sol eol count=768 ]
[ 1325.524144] cx88[0]:   iq e: 0xb3d7d800 [ arg #1 ]
[ 1325.524147] cx88[0]:   iq f: 0x18000200 [ write sol count=512 ]
[ 1325.524153] cx88[0]:   iq 10: 0x00180c00 [ arg #1 ]
[ 1325.524155] cx88[0]: fifo: 0x00180c00 -> 0x183400
[ 1325.524157] cx88[0]: ctrl: 0x00180400 -> 0x180460
[ 1325.524160] cx88[0]:   ptr1_reg: 0x00181420
[ 1325.524163] cx88[0]:   ptr2_reg: 0x00180468
[ 1325.524165] cx88[0]:   cnt1_reg: 0x00000044
[ 1325.524168] cx88[0]:   cnt2_reg: 0x00000000
[ 1325.524176] cx88[0]/0: [ffff8800c585d400/0] timeout - dma=0xad82e000
[ 1325.524179] cx88[0]/0: [ffff8800c585c400/1] timeout - dma=0x9159d000
[ 1429.823884] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 1440.846231] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 2302.239083] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 2308.494582] [drm:i915_getparam] *ERROR* Unknown parameter 6
[/INDENT]

I'm not sure exactly what I'm looking at in this dmesg log, so I just included it all.

Any ideas?

---

### Post by azmyth on 2010-01-18
Are you in the US or Europe? As I noticed your video is set to PAL which is used in Europe whereas US uses NTSC. Don't even know if this will cause you problems. I also noticed your output said mono may try a --set-tuner=stereo see

[http://ivtvdriver.org/index.php/V4l2-ctl](http://ivtvdriver.org/index.php/V4l2-ctl)

Other than this, someone with the tuner card you have is going to need to help you since I've reached my end on what to try. Good luck.

I'd also try posting on the mythtv-users list. You can search the list here.

[http://www.gossamer-threads.com/lists/mythtv/](http://www.gossamer-threads.com/lists/mythtv/)

---

### Post by platticus on 2010-01-18
Still no luck, I'm getting awfully frustrated (almost considering going back to Windows XP MCE ](*,))

But alas, I will keep trying and I will be sure to post back if I find a solution. 

In the mean time, thank you very much **azmyth**, for all your patience and guidance in my quest.

---

### Post by azmyth on 2010-01-18
Hardware is the toughest part about linux. I searched and people have gotten your tuner to work it's just a matter of finding the solution to make it work and having the patience to see it through.

Also you could try

cat /dev/video0 > file.mpg

and open the file.mpg in mplayer to see what you get.

---

### Post by platticus on 2010-05-08
Well it's been quite awhile since I was able to work with the mythbuntu machine due to a busy semester of school. But I did come across this wiki: [http://www.linuxtv.org/wiki/index.php/Cx88_devices_(cx2388x](http://www.linuxtv.org/wiki/index.php/Cx88_devices_(cx2388x)) relating to the capture card I have.

here's the output of lspci -v | grep -i audio
```
platticus@platticus-mythtop:~$ lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
02:04.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:04.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
```

The problem at the moment, seems to follow from the wiki, that my priority of devices is off and that's why I'm not getting sound with LiveTV. However, I CANNOT locate the modprobe.conf file that the wiki mentions to modify these settings.

Any ideas?

---

