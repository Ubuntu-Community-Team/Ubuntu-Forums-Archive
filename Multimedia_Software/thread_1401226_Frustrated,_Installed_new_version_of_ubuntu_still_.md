---
title: "Frustrated, Installed new version of ubuntu still can't get sound to work"
date: 2010-02-07
forum: Multimedia Software
---

### Post by duhglas on 2010-02-07
Hey I updated to new version of ubuntu a while ago, sound didn't work tried some different things to get sound working still nothing though. So I'm at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) , which is the comprehensive sound solution guide but I'm not gettin it working. I entered in 'asplay -l' in the terminal, it said  'aplay: device_list:223: no soundcards found...'. I proceeded to enter in 'lspci -v' and it came back with: 

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: ca000000-cdffffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at fc00 [size=64]
	I/O ports at f800 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: nVidia Corporation Device 0162
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at cfffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f0de:0162
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e000 [size=16]
	Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at cc00 [size=16]
	Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Memory behind bridge: cfe00000-cfefffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at cfff4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: nVidia Corporation Device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GT] (rev a2)
	Subsystem: nVidia Corporation Device 053c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at cc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at ca000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at bc00 [size=128]
	[virtual] Expansion ROM at cd000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

04:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: Micro-Star International Co., Ltd. Device b834
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at cfef8000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci


Not sure what this all means, I did download the nvidia driver for this video card, but i'm not sure what application to install it with.
I'm very frustrated at this point, I've been trying to get this workign for a couple of weeks now on and off, figured I could figure it out myself through guides and old posts but havn't been able to yet. I'm using vista on another drive but I dont like windows and would like to get back to using ubuntu most of the time. Thanks for any help.

---

### Post by 23dornot23d on 2010-02-07
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
    Subsystem: nVidia Corporation Device 0162
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at cfff4000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

________________________________________________________________

If its just the sound you cannot get working ..... and it worked before a update

open a terminal window

type in ......

sudo alsaconf

hope this helps for the sound .....  let me know if it works........

___________________________________________________________

Mine is this one and it works from alsa ok .... it too stopped working last week after a upgrade .....

My sound is fine now after running  ..........  alsaconf ......
pulseaudio does not seem to work for me ....

__________________________________________________________________________

keith2@keith-laptop:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
keith2@keith-laptop:~$ 



00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0142
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by duhglas on 2010-02-07
I typed that into the terminal and got this:
jordan@jordan-desktop:~$ sudo alsaconf
sudo: alsaconf: command not found

---

### Post by 23dornot23d on 2010-02-07
ok its not installed 

type

sudo apt-get update

sudo apt-get install alsa-utils

sudo apt-get install alsa-base

then 

sudo alsaconf



For more info about ALSA ..... go here .... [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

---

### Post by duhglas on 2010-02-07
Ok I entered in those commands and this is what happened:
jordan@jordan-desktop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_CA   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic Release.gpg                 
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Translation-en_CA [12.0kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_CA          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_CA    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release         
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Translation-en_CA [2,799B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Translation-en_CA [663B]    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Translation-en_CA           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates Release.gpg                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Translation-en_CA       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 15.5kB in 1s (10.1kB/s)
Reading package lists... Done
jordan@jordan-desktop:~$ sudo apt-get install alsaconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsaconf
jordan@jordan-desktop:~$ sudo alsaconf
sudo: alsaconf: command not found

---

### Post by 23dornot23d on 2010-02-07
sorry ....  
(for more info on ALSA ,,,, see here  [http://www.alsa-project.org/main/index.php/Main_Page )]("http://www.alsa-project.org/main/index.php/Main_Page")

type these in a terminal .....

_____________________________

sudo apt-get install alsa-utils

sudo apt-get install alsa-base

then 

sudo alsaconf

This should find your device ..... then choose it ,,,, and set it up .....

you should then have sound .....

---

### Post by duhglas on 2010-02-07
sorry my fault, misread that first time. Ok i entered in those it said they were already installed, and still when i entered 'sudo alsaconf' it came in with command not found.


jordan@jordan-desktop:~$ sudo apt-get install alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-utils is already the newest version.
The following packages were automatically installed and are no longer required:
  kdebase-runtime-data-common libqt4-qt3support libqt4-phonon libxine1-x
  libqt4-script libknotificationitem1 libqt4-designer libqt4-dbus kdelibs5
  libxcb-xv0 libexiv2-5 libqt4-opengl khelpcenter4 liblzma0 libsoprano4
  kde-icons-oxygen libclucene0ldbl phonon-backend-xine libxine1-console
  soprano-daemon libqt4-sql libqt4-svg libqt4-xml libplasma3
  libxine1-misc-plugins kdelibs-bin libstreams0 libqt4-webkit imagemagick
  exiv2 kdelibs5-data kdebase-runtime binutils-static libqt4-sql-mysql
  libxcb-shape0 libxcb-shm0 kdebase-runtime-data kdebase-runtime-bin-kde4
  libxine1-bin libstreamanalyzer0 libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 42 not upgraded.
jordan@jordan-desktop:~$ sudo apt-get install alsa-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-base is already the newest version.
The following packages were automatically installed and are no longer required:
  kdebase-runtime-data-common libqt4-qt3support libqt4-phonon libxine1-x
  libqt4-script libknotificationitem1 libqt4-designer libqt4-dbus kdelibs5
  libxcb-xv0 libexiv2-5 libqt4-opengl khelpcenter4 liblzma0 libsoprano4
  kde-icons-oxygen libclucene0ldbl phonon-backend-xine libxine1-console
  soprano-daemon libqt4-sql libqt4-svg libqt4-xml libplasma3
  libxine1-misc-plugins kdelibs-bin libstreams0 libqt4-webkit imagemagick
  exiv2 kdelibs5-data kdebase-runtime binutils-static libqt4-sql-mysql
  libxcb-shape0 libxcb-shm0 kdebase-runtime-data kdebase-runtime-bin-kde4
  libxine1-bin libstreamanalyzer0 libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 42 not upgraded.
jordan@jordan-desktop:~$ sudo alsaconf
sudo: alsaconf: command not found

---

### Post by msrinath80 on 2010-02-07
Try sudo /usr/sbin/alsaconf

---

### Post by duhglas on 2010-02-07
jordan@jordan-desktop:~$ sudo /usr/sbin/alsaconf
sudo: /usr/sbin/alsaconf: command not found

---

### Post by duhglas on 2010-02-07
ok I'm removing alsa-utils and alsa-base, and going to reinstall those see if that makes a difference, and if anything will work

---

### Post by 23dornot23d on 2010-02-07
Ok seems that alsa-tools are not loaded ...... load them in from here .....

[ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.22.tar.bz2](ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.22.tar.bz2)

---

### Post by duhglas on 2010-02-07
Reinstalling those didn't make a difference still cannot find alsaconf

---

### Post by 23dornot23d on 2010-02-07
I think you will need to do a bit of work here ,,,, 

I have already been through this process .... to get mine working ,,,, it may take a
bit of work and patience ..... but we will get your sound working ....

choose the link and download the latest version of alsa ...... tools

[ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.22.tar.bz2](ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.22.tar.bz2)

we will get the latest drivers too ......

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2)


Let me know when you have downloaded these files .....

we will then extract them into your home directory ......

---

### Post by duhglas on 2010-02-07
I clicked the link, downloaded the alsa-tools-1.0.22.tar.bz2(read only), i saved that and opened it up. No idea what to do with it, opened up a bunch of files i have no idea what they are.

---

### Post by duhglas on 2010-02-07
sorry i keep misreading these for some reason, and missing parts, ok i've got them both dl'd now  how do i extract them to home directory.

---

### Post by 23dornot23d on 2010-02-07
Ok when you open them you will see extract **all files** ........

it will ask you where to ......

Choose .... the directory as below .... its usually your name in the brackets
depending how you set it up .....

/home/(yourname)/

it should put them into there own directories once you choose to extract them ......

---

### Post by duhglas on 2010-02-07
ok i've extracted both files

---

### Post by 23dornot23d on 2010-02-07
ok can you see the directories for the 

Alsa drivers using your file viewer Nautilus/Dolphin or Thunar ......... 

go into the Alsa drivers directory ..... there you will find a file named configure

double click it ...... and it will open up a window to run it .....

choose run in terminal window .......

---

### Post by duhglas on 2010-02-07
i cannot find a file viewer, do i need one, cause i can access the configure file anyway, i jsut can't get it to open in terminal.

---

### Post by 23dornot23d on 2010-02-07
Can you show me what you are looking at now ..... use ksnapshot ...... and post a screenshot if you can .... 

use this link to upload a snapshot .... [http://tinypic.com/](http://tinypic.com/) ..... its quick and easy .....
_______________________________________________________________

We can work from the terminal .... if you know how to get to the file ok ,,,,,

So as long as you can see it and are in the directory with it in type ...... if alls ok just type .... ls

(just to check you can see the file ..... then if you can type  )

./configure

let me know if it completes ok ........



should look something like this ...... I am doing it at the same time as you are ,,,,, the bottom line
is what you are going to type in ....... 

./configure 

[IMG]http://i45.tinypic.com/6yju5z.png[/IMG]

I have already run it once to make sure its ok ........



Looks like I may have lost you for the time being ...... if you return ...... we will continue ........


I did a search on your sound card ..... for solved and alsa .... these were the results .......

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-GB%3Aofficial&hs=qme&q=alsa+utils+MCP51+solved&aq=f&aqi=&oq=]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-GB%3Aofficial&hs=qme&q=alsa+utils+MCP51+solved&aq=f&aqi=&oq=")

You will still possibly need to install the latest drivers as I did .... and then we are nearly there .......

---

### Post by duhglas on 2010-02-07
Yeah i'm having a lot of trouble here sorry for delay i can't get it open in terminal, i can get the file open, let me know if it's right or what. I did download the dolphin file viewer.
Here's the pic
where do I type the ./configure? In the terminal, cause that's not working. I'm not sure where to type it.

---

### Post by 23dornot23d on 2010-02-07
so its easier ..... use Thunar .... then we are both using the same thing it will be easier 

sudo apt-get install thunar 

then when you double click the file it will run instead of opening it and displaying it 
as what has happened using dolphin .......

I will add a screenshot here of what it looks like ........


[IMG]http://i47.tinypic.com/30idq2x.png[/IMG]


or easier still using 

[B]Dolphin ........  ( top menu bar )

Tools ..... Open Terminal[/B]



and we can work from a terminal ......

---

### Post by duhglas on 2010-02-07
I'm not sure what's wrong here but im running thunar now. This is what it looks like, I tried double clicking the configure file but it didn't do anything. I right clicked on it to see if i could get it running in the terminal but couldn't see anything.

---

### Post by 23dornot23d on 2010-02-07
Ok press Execute ..... it probably worked .... you will see the files move about a bit as
it adds new ones in the directory ....

did you see the bottom of my last post ....... ( I quickly checked Dolphin to see if we could use it better )

using Tools in Dolphin ..... you can easily get to the terminal window  ....
do it from here ..... and we can see what is happening better ,,,, and
if we need screen shots they will be more useful to me ..... ty 

[B]Dolphin ........  ( top menu bar )

Tools ..... Open Terminal

[IMG]http://i49.tinypic.com/2q325v8.png[/IMG]

./configure
make
make install

these are the commands to complete the task ......

Then we do similar in the other directory too .....

ALSA-TOOLS
[/B]

---

### Post by duhglas on 2010-02-07
I'm not sure what's wrong here, but I can't even get the terminal open inside of dolphin (snapshot). I clicked execute in thunar, and it didn't seem to do anything.

---

### Post by 23dornot23d on 2010-02-07
Try this to get the terminal ..... then it may load ......

**sudo apt-get install terminal.app**

also this ..... just looked ..... you need this one ...... 

konsole is what is missing on your system .....

[B]sudo apt-get install konsole

___________________________

[/B][http://wiki.debian.org/alsaconf](http://wiki.debian.org/alsaconf)

---

### Post by duhglas on 2010-02-07
Ok i installed 'konsole' terminal and got it working. Using dolphin I opened the terminal and ran the ./configure file and it worked. Then when i entered in the make command it said

make all-deps
make[1]: Entering directory `/home/jordan/alsa-driver-1.0.22.1'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/jordan/alsa-driver-1.0.22.1'

Please, run the configure script as first...

---

### Post by 23dornot23d on 2010-02-07
you need to do these as seperate commands ........ after one completes ..... then you type the next ......

./configure

,,,,,,,,,,(run,,,, output)

make

,,,,,,,,,(run,,,, output)

make install

---

### Post by duhglas on 2010-02-07
Ok i did that and it says this, it doesn't look like it's completing the installation but I'm not sure

jordan@jordan-desktop:~/alsa-driver-1.0.22.1$ ./configure make                  
configure: WARNING: you should use --build, --host, --target                    
checking for make-gcc... no                                                     
checking for gcc... gcc                                                         
checking for C compiler default output file name... a.out                       
checking whether the C compiler works... yes                                    
checking whether we are cross compiling... no                                   
checking for suffix of executables...                                           
checking for suffix of object files... o                                        
checking whether we are using the GNU C compiler... yes                         
checking whether gcc accepts -g... yes                                          
checking for gcc option to accept ISO C89... none needed                        
checking for make-ranlib... no                                                  
checking for ranlib... ranlib                                                   
checking for a BSD-compatible install... /usr/bin/install -c                    
checking how to run the C preprocessor... gcc -E                                
checking for grep that handles long lines and -e... /bin/grep                   
checking for egrep... /bin/grep -E                                              
checking for ANSI C header files... yes                                         
checking for an ANSI C-conforming const... yes                                  
checking for inline... inline                                                   
checking whether time.h and sys/time.h may both be included... yes              
checking whether gcc needs -traditional... no                                   
checking for current directory... /home/jordan/alsa-driver-1.0.22.1             
checking cross compile...                                                       
checking for directory with ALSA kernel sources... ./configure: line 5107: cd: ../alsa-kmirror: No such file or directory                                       
../alsa-kmirror                                                                 
checking for directory with kernel source... ./configure: line 5132: cd: /usr/src/linux: No such file or directory                                              
/usr/src/linux                                                                  
checking for directory with kernel build...                                     
checking for kernel linux/version.h... no                                       
The file /include/linux/version.h does not exist.                               
Please install the package with full kernel sources for your distribution       
or use --with-kernel=dir option to specify another directory with kernel        
sources (default is /usr/src/linux).                                            


jordan@jordan-desktop:~/alsa-driver-1.0.22.1$ ./configure make install          
configure: WARNING: you should use --build, --host, --target                    
configure: WARNING: you should use --build, --host, --target                    
checking for make-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for make-ranlib... no
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/jordan/alsa-driver-1.0.22.1
checking cross compile...
checking for directory with ALSA kernel sources... ./configure: line 5107: cd: ../alsa-kmirror: No such file or directory
../alsa-kmirror
checking for directory with kernel source... ./configure: line 5132: cd: /usr/src/linux: No such file or directory
/usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
jordan@jordan-desktop:~/alsa-driver-1.0.22.1$

---

### Post by 23dornot23d on 2010-02-07
we are missing gcc ....... so do ..... 

[B]sudo apt-get install gcc
[/B] 

afterwards just type in ..........

**./configure**

please and show me the output .........

---

### Post by duhglas on 2010-02-07
ok i've got gcc 

jordan@jordan-desktop:~$ sudo apt-get install gcc
[sudo] password for jordan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Looks like it was already installed though

---

### Post by 23dornot23d on 2010-02-07
what happened was you entered two commands .... (./configure make) at the same time .... it confused it

I think .....

just type this one first .....

**./configure**

---

### Post by duhglas on 2010-02-07
Ok I'm using 2 different terminals right now. The regular one which i entered the gcc command in. Then the 2nd is the one I opened through dolphin, which is the 'jordan@jordan-desktop:~/alsa-driver-1.0.22.1$'. So in the 2nd terminal i've tried the 
./configure   .....
./configure make          .........
./configure make install     ...... 
and still same result as last time


I've tried entering in the make command as well, but it says

make all-deps
make[1]: Entering directory `/home/jordan/alsa-driver-1.0.22.1'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/jordan/alsa-driver-1.0.22.1'

Please, run the configure script as first...



so thats why i enter ./configure make

---

### Post by 23dornot23d on 2010-02-07
nope ..... do not put ./configure before make

**make** ...... is a separate command 

( let me know if it flags up errors though ..... it appeared to not be finding your kernel in your previous output )
[B]


make install[/B] ......... and so is make install .....

______________________________________________________________________________

once you complete everything and have ALSA-TOOLS and Libraries loaded
type this see if it gives any output ..... hopefully alsaconf is in here ,,,, (this is the file you need)

[B]ls /usr/sbin/alsaconf

sudo alsaconf

[IMG]http://i48.tinypic.com/1zn50s2.png[/IMG]


Then you will see this after it builds a database of all available cards ....

[IMG]http://i46.tinypic.com/2i2bjg4.png[/IMG]


[/B]

---

### Post by duhglas on 2010-02-07
I've tried entering in the make command as well, but it says

jordan@jordan-desktop:~/alsa-driver-1.0.22.1$ ./make
bash: ./make: No such file or directory
jordan@jordan-desktop:~/alsa-driver-1.0.22.1$ make
make all-deps
make[1]: Entering directory `/home/jordan/alsa-driver-1.0.22.1'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/jordan/alsa-driver-1.0.22.1'

Please, run the configure script as first...



so thats why i enter ./configure make

---

### Post by Yellow Pasque on 2010-02-07
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by 23dornot23d on 2010-02-07
Thanks for the link above ....... best to look here ......


there is something else ..... wrong here ,,,, and I am not sure what ,,,,
mine runs ok and yet yours appears not to find the kernel sources .....


[I][B]checking for directory with kernel build...                                     
checking for kernel linux/version.h... no                                       
The file /include/linux/version.h does not exist.                               
Please install the package with full kernel sources for your distribution


THE ABOVE LINK IS PROBABLY THE ANSWER


[/B][/I]

---

### Post by duhglas on 2010-02-07
Yeah it seems like something is wrong with mine. I'm not sure if I updated to the latest version of 9.04 before i updated to koala, which i recently read you're supposed to do. As well, the first time when I was trying to fix this problem, I was following some instructions on the forum, of a solved post, and I never completed it before I couldn't continue on. 
So I'm not sure if everything is good or not. I was thinking of doing a fresh clean install as i havn't done much on this computer and wouldn't be thrilled, but wouldn't mind reinstalling. I was checking out that link, but right now my brain's a little tired, and I don't wanna start a whole other process tonight. Are we making progress here? Or have we reached a snare, that we may not get past?
Would you know the method to install the full kernel package 23? Would we be able to get it done tonight?

When I boot up with grub it loads the 9.04 version of ubuntu, does that matter?

---

### Post by 23dornot23d on 2010-02-08
I have reached a dead end as such ......

alsaconf and the latest libraries are what you need IMHO ,,,,,,

but what is the easiest way to get them ...... maybe the link above ...... or ...

Maybe 9.10 ..... will already detect the sound card  ..... or maybe have alsaconf installed

so that you can use it to set up the sound card  ....... its upto you .......

If you have enough space on your hard drive ...... you could triple boot

I keep Ubuntu 8.10 running on here too ...... and it runs like a dream never gives me a problem ....

........... as well as Mandriva 2010 which was an upgrade from Mandriva 2009 Spring edition .....

I upgraded 9.04 to Ubuntu 9.10 but previously lots of problems sound being just one .....  ALSA sorted that for me ....

Best to do a clean install of 9.10 from what I have read ...... as upgrades seem to rarely go smoothly .......

and keep your home drive on a seperate partition ..... keeps all your user files seperate ......


But ..........it  All depends on how much Hard Drive space you have .......... and whether or not this is what you would want.

I hope this helped a bit ...... sorry I could not help more ..... 

I am pretty sure ALSA will solve the problem you have though ,,,, as regards sound not working .....

---

### Post by duhglas on 2010-02-08
I have 2 seperate hard drives I use for vista and ubuntu. I have a 160gb drive for ubuntu and 320gb for vista. I play to start using ubuntu almost exclusively as I'm really sick of windows. I could put vista on the 160 gb and ubuntu on 320gb. I need to reinstall vista as it's in real bad shape right now. So I may just switch the 2 and do fresh installs on both. I will have to back up the systems this tiem as that is something i never do and i always wish i would. So I may do that. Or I'll keep workign on this and see if i can fix it, but i think this is my best option. I will look into it more tomorrow however, and see if i can make any progress.
Thanks a lot for the help though, I really appreciate it, atleast I learned a lot about working with ubuntu even if we didn't solve the problem.

---

### Post by 23dornot23d on 2010-02-08
Ok thanks .... glad it was useful for learning your way around Ubuntu ,,,, hope you get it sorted and with the room you have on the hard drives .... 

its plenty to have 3 operating systems running ..... thats if you want ..... 

Mandriva 2009 Spring edition is pretty good at picking all things up ok ....... for me ..... 

as was Ubuntu 9.04 .....

9.10 as a upgrade from 9.04 was a lot of hard work for me personally ..... but its all a learning experience .....

I really hope to see you with your system up and running as you would like it  ;)  all for now ...... have fun .....

---

### Post by duhglas on 2010-02-08
23dor are you around. I've got to the point now where I've got the alsaconf working. As well I've got the latest alsa driver configuration open. Not sure what I need to do here. Can anyone guide me through this?
I'm also working on this [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137) . But I dont think I'm doing it correctly. Im dl'd the alsa-driver-1.0.22.1.tar.bz2 file and trying to get that running, but I'm having a lot of trouble. I'm still rather clueless when it comes to ubuntu, so that's probably why I'm having so many problems here, thanks for any help.

---

### Post by 23dornot23d on 2010-02-08
Hi I am here now if you need help with this ...

[B]sudo alsaconf

[IMG]http://i48.tinypic.com/1zn50s2.png[/IMG]


Then you will see this after it builds a database of all available cards ....

[IMG]http://i46.tinypic.com/2i2bjg4.png[/IMG]

OK does not seem like you are here ..... here is another link .....
[/B]
OK so this is the easiest way ..... a PPA .... to add to Karmic sources list ....... 

( NOTE : it says to remove after using  for this task ......... ) 

**DIRECT LINK to PPA .......**[https://launchpad.net/~ricotz/+archive/unstable]("https://launchpad.net/%7Ericotz/+archive/unstable")

Information on how to use it .......[http://www.webupd8.org/2010/01/upgrade-to-alsa-1022-and-more-in-ubuntu.html](http://www.webupd8.org/2010/01/upgrade-to-alsa-1022-and-more-in-ubuntu.html)

**a) Only upgrade the packages you want and then remove the PPA:**

This should get all the latest programs and files ........ [COLOR=Red]***but remove from your sources list once done***[/COLOR] .......

I hope that you have sound now .....

---

