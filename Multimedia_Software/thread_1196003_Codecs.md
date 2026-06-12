---
title: "Codecs"
date: 2009-06-24
forum: Multimedia Software
---

### Post by papabill on 2009-06-24
I've been trying to get the "built-in" DVD player to work, but cannot get the codecs for it. It goes through a download and install procedure, but nothing works. 

I have a LiteOn DVD/CD DVD-R/DVD-RW installed on 8.04-1.

Ideas please??

---

### Post by .Maleficus. on 2009-06-24
Are you using ubuntu-restricted-extras?

---

### Post by papabill on 2009-06-24
I'm new to Linux, so I don't know what those are or how to get them.

---

### Post by .Maleficus. on 2009-06-24
ubuntu-restricted-extras is a codec package with support for MP3 playing and video codecs, among other things.  Open a terminal and enter:
```
sudo apt-get install ubuntu-restricted-extras
```
And are you trying to play a physical DVD or a ripped video file?

---

### Post by papabill on 2009-06-24
> **.Maleficus. said:**
> ubuntu-restricted-extras is a codec package with support for MP3 playing and video codecs, among other things.  Open a terminal and enter:
```
sudo apt-get install ubuntu-restricted-extras
```

Already did that-still nothing.

Either one would be nice-I've tried playing a DVD directly in the DVD player, and I've tried copying one that was copied to disc and playing it. Nothing happens either way.

First thing i get when I try to play from DVD player is "An error occurred-could not read from resource"-(I just copied it onto a Windows machine, so I know the disc is good, and the DVD player is new, so I know it's good too)

---

### Post by xc3RnbFO8P on 2009-06-24
If you are using Hardy 32 bit:
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
> sudo apt-get install libdvdcss2 
> sudo apt-get install w32codecs 
> sudo apt-get install libdvdread3
 > sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by papabill on 2009-06-24
> **Ringi said:**
> If you are using Hardy 32 bit:

Went through all as instructed. Still nothing happening.

---

### Post by .Maleficus. on 2009-06-24
If you don't mind having another program installed, VLC media player will play them out-of-the-box.  It should be in the repos so...
```
sudo apt-get install vlc
```
or search 'vlc' in Synaptic.

---

### Post by papabill on 2009-06-24
Nope, that was one of the first ones I was advised to install, and even it doesn't work.

Thanks

---

### Post by mc4man on 2009-06-25
Open vlc from a terminal, the 0.8.6 ver. in hardy can produce some decent error messages.

Just type vlc in the terminal, press enter and then open your dvd from vlc. (it's been a while since I used 0.8.6 - Probably file -> open disc.

Vlc will default to /dev/scd0 as the dvd device, if your not sure that's your device then first run this and check under the *-cdrom  listing
```

sudo lshw -C disk
```

post the complete terminal output from attempting to play a dvd in vlc

---

### Post by papabill on 2009-06-25
root@Ubuntu:/home/bill# vlc
VLC media player 0.8.6e Janus
starting VLC root wrapper... using UID 1000 (bill)
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat /dev/scd1
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/scd1
[00000292] main input error: no suitable access module for `dvd:///dev/scd1'
[00000283] main playlist: nothing to play
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat /dev/scd1
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000306] dvdread demuxer error: DVDRead cannot open source: /dev/scd1
[00000305] main input error: no suitable access module for `dvd:///dev/scd1'
[00000283] main playlist: nothing to play
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: ENTERPRISE S1D7
libdvdnav: DVD Serial Number: 3ABAA53B
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/root/.dvdnav/ENTERPRISE S1D7.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000131
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000203
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000023a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00007bda
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0011f2fc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001267b9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00212dfb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0021733c
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
[00000363] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
E: authkey.c: Failed to open cookie file '/root/.pulse-cookie': No such file or directory
E: authkey.c: Failed to load authorization key '/root/.pulse-cookie': No such file or directory
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  108
  Current serial number in output stream:  109
root@Ubuntu:/home/bill#

---

### Post by raboofje on 2009-06-25
> **papabill said:**
> root@Ubuntu:/home/bill# vlc

Try as non-root.

---

### Post by xc3RnbFO8P on 2009-06-25
Try this:
> * VLC (VLC is not installed by default; you need to search in the package manager, then install)
o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set!

---

### Post by papabill on 2009-06-25
nope, that didn't work either. I'm beginning to think there is something about the hardware that is NON-Linux compatable.

---

### Post by xc3RnbFO8P on 2009-06-25
What is your computer spes.?

---

### Post by papabill on 2009-06-25
HP Pavilion XE783 PC bundle 

Model number
P1372A
Base processor and speed
Intel (R) Celeron 700 MHz processor (socket 370)
Maximum HP supported replacement: Intel Celeron 700 MHz
Chipset
Intel 810
Memory
Component  Attributes  
RAM (standard)  64 MB PC 100  
Maximum  512 MB (2 x 256 MB DIMMs)  
Speed  100 MHz synchronous  
Sockets  Two 168-pin DIMMs  
Size  32, 64, 128, and 256 MB DIMMs  
Pairs Required  No  
Free DIMM socket  1  
Type Supported  SDRAM

100 MHz, Intel PC SDRAM unbuffered DIMM specification, revision 1.0 compliant  

 NOTE:  Free DIMM slots may vary due to availability of memory components at the time the PC is manufactured.  

Cache
Level  Quantity  
Level 1 (Primary)  32 KB (on processor)  
Upgrade Sockets  None  
Level 2  128 KB (on processor)  

Hard drive
30 GB (3.5” form factor)
DVD Family Write 
DVD+R 22X  
 
DVD-R 22X 
 
DVD+R9 8X   
 
DVD-R9 8X  
 
DVD-RAM 12X  
 
 
ReWrite 
DVD+RW 8X   
 
DVD-RW 6X    
 
Read 16X  
 
Access time 160ms 
CD Family Write 
CD-R 48X  
 
ReWrite 
CD-RW 32X  
 
Read 48X  
 
Access time 140ms 
Buffer Size 2MB (MAX) 
PC Required Pentium 166 MHz or higher CPU and 128MB or higher RAM are
required. 
HDD must have access time < 20ms; with a minimum of 650MB free
space. 
9GB free space for creating a DVD image file (9GB for double layer;
5GB for single layer). 
Compatibility MS 2000/ XP/ Vista 
MTBF (Life) 70000POH 
S/N Ration > 75dB 
General Environment 
Operating 5°C to 50°C; Relative Humidity: 15% to 80% 
Non-Operating -40°C to 65°C; Relative Humidity: 15% to 95% 
Dimension 145(W) x 41.3(H) x 170(D) mm 
Weight < 0.9Kg 
Voltage Requirements 
+5V +/-5% and less than 100 mVp-p ripple voltage 
+12V +/-5% and less than 200 mVp-p ripple voltage 

Diskette drive
1.44 MB (3.5-inch form factor)
Fax/data modem
Attribute  Properties  
Modem  Cheetah

(supports V.90 K56 Flex protocols)  
Data Speed  56 Kbps  
Fax Speed  Up to 14.4 Kbps  
Plug and Play  Yes  
Hayes Compatible  Yes  
Data Compression  v.42 bis  
Error Correction  v.42  
COM Port (default)  2  
IRQ (default)  Variable  
EIA Fax Commands  Class 1  

Video
Attribute  Properties  
Video Graphics  PCI Local Bus  
Controller  Intel 810 (on motherboard)  
Video Memory  11 MB shared system memory, integrated graphics, not upgradeable  
Feature Connector (game/joystick)  Yes  
Resolutions:  640 x 480: 16/256/32 K/64 K/16.7 M colors

800 x 600: 16/256/32 K/64 K colors

1024 x 768: 16/256/32 K/64 K colors

1280 x 1024: 256 colors  

MPEG-1/2
MPEG-1 for full-screen, full-motion digital video
Sound/audio
Attribute  Properties  
Compatibility  3-D Stereo, PCI, 16-bit Sound  
Controller  AMC97 Codec  
Location  Crystal sound chip  
Noise Cancellation  Yes  
Line Out  Yes  
3-D Spatializer  Yes  
Wavetable  Yes  
Tone Control  No  
Microphone  With HP Pavilion Multimedia Display  
Speakers  HP/Polk Audio "F" stereo speakers (left and right)  

External ports
Total external ports 
Port type  Quantity  
USB  2  
Serial  1  
Parallel  1  
Game  1  

Front panel I/O 
Port type  Quantity  
Serial  1  

Expansion slots
Total expansion slots 
Port type  Quantity  
PCI  3  

Available expansion slots 
Port type  Quantity  
PCI  2  

Drive bays
Total drive bays 
Bay Type  Quantity  
3.5-inch, external  2  
5.25-inch, external  1  
3.5-inch, internal  1  

Free drive bays 
Bay Type  Quantity  
3.5-inch, external  1  

Power supply information
AC input 
90 Watts
Input Frequency: 50/60 Hz
Voltage: 120V (100-120V) ~ 3A / 0
Voltage: 230V (200 - 240V) ~ 1.5A
Power supply output 
DC Voltage  Current  
+12V  1.5 A  
+5V  10 A  
+3.3V  6 A  
-12V  0.2 A  
+5VSB  0.72 A  

Keyboard and mouse
HP PS/2 One-touch multimedia keyboard
HP PS/2 2-button mouse

From lshw:
ubuntu
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 382MiB
     *-cpu
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.3
          size: 700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KiB
     *-pci
          description: Host bridge
          product: 82810 GMCH (Graphics Memory Controller Hub)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82810 (CGC) Chipset Graphics Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-pci
             description: PCI bridge
             product: 82801AA PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 3c905 100BaseTX [Boomerang]
                vendor: 3Com Corporation
                physical id: a
                bus info: pci@0000:01:0a.0
                logical name: eth0
                version: 00
                serial: 00:10:4b:22:e0:85
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.0.2 latency=64 link=yes maxlatency=8 mingnt=3 module=3c59x multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801AA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801AA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: Maxtor 33073U4
                vendor: Maxtor
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BAC5
                serial: N40T359C
                size: 28GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c730c730
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 845c9e83-6c71-4ebb-9748-16f4a9452400
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-06-23 13:22:06 filesystem=ext3 modified=2009-06-24 11:51:23 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-06-24 11:51:23 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1090MiB
                   capacity: 1090MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1090MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: iHAP322   8
                vendor: ATAPI
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: UL14
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
                   logical name: /media/cdrom0
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
        *-usb
             description: USB Controller
             product: 82801AA USB Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: 82801AA SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801AA AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

---

### Post by kristan2000 on 2009-06-28
EMDB is a small utility to keep track of your DVD collection. With an automatic import from the database of IMDB, export to csv, text or complete website, thumbnail cover preview, a loan tracker, search function and multi-language user interface.
=========================================
[wasserbett]("http://www.wasserbettenhilfe.com")
[taxi from toronto airport to toronto]("http://www.torontoairportcab.com/html/services.htm")

---

