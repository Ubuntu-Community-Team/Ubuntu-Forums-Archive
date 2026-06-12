---
title: "Inserting DVD Crashes Linux (I mean completely brings the system down!!!)"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by narnie on 2007-05-13
When I insert a DVD into my drive, it brings a complete system crash. I mean poof. Blank screen, even a pretty blue screen (ut-oh, is this a Linux BSOD?).

I have the codecs install as per the howtos. If I have the DVD in when I boot, it doesn't crash, but try to open it in Totem-Xine, Poof. Try to open it with VLC, Poof !!!. Try to open it with MPlayer and get " Error opening/initializing the selected video_out (-vo) device" but it doesn't crash.

I can't do a blessed thing but hard-reset. I can't Crtl-alt-F1 or any other function key to get to a tty or anything. Don't know if it helps, but it does make a split-second sound from the speakers (can't describe it) as it crashes.

Any ideas. I really need this DVD for my business. It is a must have and I'd prefer to run my business in Linux. The DVD, I'm sad to say for Linux's sake, works fine under the Vista partition on the same computer.

TIA,
Narnie

PS, just tell me what you need as far as info to help me. Thanks.

---

### Post by RomeReactor on 2007-05-13
Hi. That's a new one for me... Anyway, i don't know why Totem or VLC are crashing, but in the case of Mplayer, I think you can fix it: open Mplayer, right-click on it and select "Preferences"; go to the "Video" tab, and select **XV    X11/Xv** as the video driver. Close mplayer and open it again for the changes to take effect, and try playing that DVD now. 

For Totem, do you have Universe, Multiverse and Medibuntu repositories enabled? and did you install libdvdcss and the other [required packages]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability")? If not:

Open a terminal (Applications-->Accessories-->Terminal) and enter the following:

```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O - | sudo apt-key add -
```

that adds Medibuntu's gpg key to your system's list of trusted APT keys; then

```
gksudo gedit /etc/apt/sources.list
```

which will open your repositories list in a text editor; add the following at the end of the file (if it's not there already):

```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

Save the file and close the text editor. If you don't know if you have Universe and Multiverse repositories, open Synaptic (System-->Administration-->Synaptic Package Manager), go to "Settings-->Repositories" and on the first tab (Ubuntu Software) make sure all the boxes are checked. Close Synaptic, and enter this in the terminal:

```
sudo apt-get update
```

to update your software database with the newly added repositories. Then:

```
sudo apt-get install libxine1 libxine1-ffmpeg libxine-extracodecs libxinerama1 libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3
```

If you haven't installed those, they'll probably take care of the issue. Are you absolutely sure you have **totem-xine** installed?

---

### Post by narnie on 2007-05-14
BTW, forgot to mention this is a laptop. and using edgy eft (worked too hard to get this where I want it and have seen too many things breaking to want to upgrade to feisty yet).

My hardware is reported as follows:

May 13 22:53:50 Aspire kernel: [17179574.204000]   Vendor: TSSTcorp  Model: CD/DVDW TS-L632D  Rev: AC01
May 13 22:53:50 Aspire kernel: [17179590.184000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

I manually checked on each of the above libs/codecs and found only libxine1-ffmpeg not to be present. I've apt-get updated and it is not there. Is it feisty only?
I didn't have medibuntu in the repos, but I added it.

Thanks for the tip on MPlayer. I'll try it out and post back.

Also on Totem-xine. When I click on about, I get Totem Movie Player 2.16.2 Movie Player using xine-lib version 1.1.2 and GNOME

BTW, how do I disable autoplay of a DVD so it doesn't start up Totem and trash my system?

Narnie

---

### Post by esoterica on 2007-05-14
I don't know if this will help you or not, but since your just waiting on a solution anyhow it may give you something to look into.

About 2 years ago I had a problem just like this when trying out Red Hat with paid support. I don't remember how now I determined it (Red Hats support was worthless), but the problem when I was having it was because of my drivers for the on board Audio card, which was a C-Media and supposedly had Linux drivers for it. I've always been a trying to get Linux to just work kind of person, never made it to having enough luck with it to actually make it stable and 100% working for me so I never became a Linux expert by any means.

I never did get that onboard audio card to work, tried everything, as soon as anything fired up though that required audio to run in one of the players the entire system would lock up and all that would undo it was hitting the power button. There had to be a fix for the problem, no one at RedHat or endless searching could ever figure it out, but the audio card did work when running from a knoppix booted CD without locking things up. I was never Linux sharp enough though to be able to figure out what driver Knoppix used on it so I could install that same one.

The point of my comment to you is not to imply it's the Audio driver causing your problem, though it could be, but instead it may be an issue with the drivers you are using. This may be a reason for you to reconsider installing Ubuntu 7.04 instead...

[http://www.desktoplinux.com/news/NS7895189911.html](http://www.desktoplinux.com/news/NS7895189911.html)

It was this claim of better hardware support that re initiated my own interest in once again giving Linux another try, though I'm still so far unable to play DVD's even after following all the documentation I could find, the system is at least stable for me though and all of my hardware is working without the need to do indepth messing with it to get it there. This is a pretty big issue when your using a laptop and can't freely pick and choose your hardware like you can with a desktop computer.

---

### Post by RomeReactor on 2007-05-14
> **narnie said:**
> I manually checked on each of the above libs/codecs and found only libxine1-ffmpeg not to be present. I've apt-get updated and it is not there. Is it feisty only?
I didn't have medibuntu in the repos, but I added it.

Yes, looks like libxine1-ffmpeg is Feisty-only. Sorry about that.

> BTW, how do I disable autoplay of a DVD so it doesn't start up Totem and trash my system?

Go to "System-->Preferences-->Removable Drives and Media", and on the second tab (Multimedia) uncheck "Video DVD Discs".

And, since you're running Edgy, the medibuntu repositories are different; this is the correct repository:

```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
```

Also, the following two commands show information about your laptop, so please post the output:

```
lspci
```
```
sudo lshw
```

And how much ram does it have?

---

### Post by narnie on 2007-05-14
I'd already changed the medibuntu to edgy. Thanks for verifying though!!! I'm still quite the noob.

lspci

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
```

sudo lshw

```
aspire                    
    description: Notebook
    product: Aspire 5610
    vendor: Acer
    version: V3.23
    serial: LXAXZ0X021650202AC1601
    width: 32 bits
    capabilities: smbios-2.33 dmi-2.33
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=504BDE06-20EF-901F-01BE-0016D46897A0
  *-core
       description: Motherboard
       product: Grapevine
       vendor: Acer
       physical id: 0
       version: N/A
       serial: LXAXZ0X021650202AC1601
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V3.23 (12/09/2006)
          size: 101KB
          capacity: 960KB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2250  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U1
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr cpufreq
          configuration: id=1
        *-cache
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 2MB
             capacity: 2MB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1GB
          capacity: 2GB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: M1
             size: 512MB
             width: 32 bits
        *-bank:1
             description: SODIMM Synchronous
             physical id: 1
             slot: M2
             size: 512MB
             width: 32 bits
     *-cpu:1
          product: Genuine Intel(R) CPU           T2250  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1733MHz
          capacity: 1733MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:d0200000-d027ffff ioport:5088-508f iomemory:c0000000-cfffffff iomemory:d0300000-d033ffff irq:177
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:d0280000-d02fffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:d0340000-d0343fff irq:66
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@05:00.0
                logical name: eth1
                version: 02
                serial: 00:18:de:53:eb:c9
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () ip=172.27.172.168 link=yes multicast=yes wireless=IEEE 802.11b
                resources: iomemory:d0100000-d0100fff irq:193
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:50a0-50bf irq:50
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:50c0-50df irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:50e0-50ff irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:5400-541f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-11-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:d0544000-d05443ff irq:50
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-11-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb
                   description: Generic USB device
                   product: Camera
                   vendor: OEM
                   physical id: 4
                   bus info: usb@5:4
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=gspca maxpower=200mA speed=480.0MB/s
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@06:01.0
                logical name: eth0
                version: 02
                serial: 00:16:d4:68:97:a0
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
                resources: iomemory:d0000000-d0001fff irq:58
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@06:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:d0002000-d0002fff irq:177
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@06:04.1
                version: 01
                width: 32 bits
                clock: 33MHz (30.303ns)
                capabilities: cap_list
                resources: iomemory:d0003000-d000307f irq:11
           *-system
                description: Generic system peripheral
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.2
                bus info: pci@06:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci
                resources: iomemory:d0003400-d00034ff irq:169
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@06:04.3
                version: 01
                width: 32 bits
                clock: 33MHz (30.303ns)
                capabilities: cap_list
                resources: iomemory:d0003800-d000387f irq:11
           *-memory:2 UNCLAIMED
                description: FLASH memory
                product: ENE Technology Inc
                vendor: ENE Technology Inc
                physical id: 4.4
                bus info: pci@06:04.4
                version: 01
                width: 32 bits
                clock: 33MHz (30.303ns)
                capabilities: cap_list
                resources: iomemory:d0003100-d00031ff irq:255
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix
             resources: ioport:5440-544f irq:193
           *-disk
                description: SCSI Disk
                product: ST9160821AS
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AL
                serial: 5MA09Q42
                size: 149GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Compaq diagnostics partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 6997MB
                   capabilities: primary boot
              *-volume:1
                   description: FAT16 partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 71GB
                   capabilities: primary bootable
              *-volume:2
                   description: HPFS/NTFS partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 41GB
                   capabilities: primary
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 29GB
                   capabilities: extended partitioned partitioned:extended
           *-cdrom UNCLAIMED
                description: SCSI CD-ROM
                product: CD/DVDW TS-L632D
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                version: AC01
                capabilities: removable
                configuration: ansiversion=5
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:5420-543f irq:10
ignite@Aspire:~$ 


```

Thanks for the continued help
Narnie

---

### Post by narnie on 2007-05-15
Just tried to load a DVD with MPlayer after doing the above tweak. It resulted in a crash with a blue screen and weird popping noises from the pc speakers.

I was going to see if Real Player would play it, but I see that it doesn't play dvds on linux.

---

### Post by narnie on 2007-05-15
Sorry, forgot to answer the memory question. 1 gb memory onboard.

---

### Post by RomeReactor on 2007-05-15
It looks like you have a Core 2 Duo running at 1.73 GHZ, an Intel Mobile 94X 256 MB video card and 1 GB of RAM; so the problem doesn't stem from lack of computing power on your laptop. Reading your lshw output, this struck me as odd:
```
*-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:d0280000-d02fffff
```
If your sound works well listening to music, then I don't think that's the issue here. Let's try this: On the terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
to make a backup of xorg.conf; then press **CTRL+ALT+F1** to get out of the xserver, then:
```
sudo /etc/init.d/gdm stop
```
to stop the xserver; then:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to reconfigure your display; now:
```
sudo /etc/init.d/gdm start
```
to start the xserver, and press **CTRL+ALT+F7** to return you to your desktop. If that breaks your graphical environment (meaning that the next time you boot your laptop it sends you straight to the command line), then do this:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
to restore the previous file, and:
```
sudo reboot
```
But first post what happens when opening the DVD with mplayer after you changed its video driver. A good way to troubleshoot misbehaving applications is to run them from the terminal and, if the application crashes, look at the messages (if any) it leaves there; in the case of mplayer:
```
gmplayer
```
then right click on it and use its menu to open the DVD. Does this happen with other DVD's or video files?

---

### Post by RomeReactor on 2007-05-15
Sorry, didn't see your answers; I took too much time with my post. Try the bit about launching mplayer from the command line.

---

### Post by narnie on 2007-05-15
Yeah, I did something stupid with my display. I was trying to compile a video driver for another laptop (hoping it would compile on this one), only it did more than compile, it tried to install.

since then, direct rendering = "no" but beryl still works without a problem (execept no water effect, which I've read is a driver problems). When I first installed Ubuntu (actually installed it b4 ever even booting Vista), I got direct rendering "yes" but I broke it. I think I already tried what you suggested, but when I get a chance, I'll do it again.

I did the crash thing again with I started MPlayer in a tty. when it crashes, there is nothing left to look at but a blue (or black) screen. There is no way for me to see what is left in the terminal, but I was hoping this exercise might have left something in /var/log/messages, but alas no. I think it fries the kernal (or something) so badly, no error login done (but I'm not sure on this).

I'd love more ideas.

what about some of the other drivers on the MPlayer Preferences?

---

### Post by RomeReactor on 2007-05-15
Sure, you can try changing Mplayer's video driver, though **XV    X11/Xv** is the one I've seen that solves most issues; can't really say about the others; I've not tried them. I've run out of ideas for now since I have no experience with Intel video cards and was kind of hoping that dpkg-reconfigure would rectify the situation. I think it's strange that almost no one else has jumped in with more suggestions... again, sorry. I would recommend that you download Feisty and give it a try from the live cd. It's more feature-complete than Edgy.

---

### Post by RomeReactor on 2007-05-15
Just thought of this: From the terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
scroll down to **Section "Device"** and look which driver it says it's using: if it's anything other than **vesa**, I think you can change it to it.
```
Driver          "vesa"
```
If I'm not mistaken, and this is a driver issue, maybe that could be a temporary solution while you find out how to uninstall the problematic drivers and install the correct ones.

---

### Post by narnie on 2007-05-16
I'll try it, but I don't want to keep vesa, because it has no 3D support, and I love my beryl, hehe.

I'll try that suggestion about reconfig. I'll also see if vesa breaks it.

I'm wondering if there are other drivers for the DVD/RW/CDRW????

---

### Post by narnie on 2007-05-19
RomeReactor,

I did the dpkg command and tried in vesa, and I was able to play DVDs !!! Then I switched back to my i810, and it still worked. I think it was the dpkg.

However, I still get display as an unclaimed device and DRI "no." But everything's working !!! Except for suspend and hibernate. I've done a lot of work on this and gotten it to work, but after time, it breaks and I'm running out of options. I'm using Edgy with NetworkManager and it'll hang my system on shutdown.

If you might be able to help, I'll tell you what I've done so far.

Thanks for all the help,
Narnie

---

### Post by RomeReactor on 2007-05-20
[This link]("http://ubuntuforums.org/showthread.php?t=326864") explains how to install another driver (converted from .rpm to .deb using **alien**), and setting up widescreen resolution with **915resolution**; I've read of people solving their rendering problems this way. Might be worth a try--but first:
```
sudo apt-get install alien 915resolution
```
Perhaps it would be a good idea to start a new thread (like "How do I enable direct rendering on Intel 945GM?" or something like that) or to ask for help on IRC (#ubuntu@irc.freenode.net). Sorry for the lack of answers, but I really have no experience with direct rendering on Intel cards.

---

### Post by H4rold on 2007-05-20
Hi,
 I have the same CDdrive and I also have problems. I think the problem comes from the CDROM.
I have Ubuntu Feisty installed and the computer crashes after some time (not very long if a CDROM is in the drive).
Basically X is frozen and if I go on a console I have "hda : drive command not ready" and I cannot do anything except reboot.
If I go in /var/log/message I have :
May 19 18:36:56 harold-laptop kernel: [ 1827.609609] hda: status timeout: status=0xd0 { Busy }
May 19 18:36:56 harold-laptop kernel: [ 1827.609616] ide: failed opcode was: unknown

sudo smartctl --all /dev/hda -T displays :
=== START OF INFORMATION SECTION ===
Device Model:     TSSTcorpCD/DVDW TS-L632D
Serial Number:    [No Information Found]
Firmware Version: AS04
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   1
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun May 20 14:35:09 2007 CEST
SMART is only available in ATA Version 3 Revision 3 or greater.
We will try to proceed in spite of this.
SMART support is: Unavailable - Packet Interface Devices [this device: CD/DVD] don't support ATA SMART
SMART support is: Unavailable - device lacks SMART capability.
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

I am not the only one having this problem ([http://forum.ubuntu-fr.org/viewtopic.php?pid=939121#p939121](http://forum.ubuntu-fr.org/viewtopic.php?pid=939121#p939121)) and I also had burning problems when I was running windows.

I suppose automount is the one responsible because if I open the CDROM drive it works.

Does anyone habe any idea ?


Edition : I did find that : [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/75295](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/75295)

---

### Post by theDaveTheRave on 2007-09-23
Hello All.

I had similar problem with DVD playback when I set the "Desktop Effects" to be turned on.

I have now tried Beryl instead and I have the same issue with that.

I don't expect to find a solution for why the DVD won't playback, I have a recolection that it is related to how the driver in Beryl works conflicts with the DVD codes (or something!?).

Anyway what I would like to know is there a way of turning off all of the Beryl effects, so as I don't have to reboot to get my DVD playback to work? and of course I assume that I can simply turn them back on again by starting up up the Beryl manager.


Is this a possible solution to DVD playback?? or am I best to create a new user that doesn't have Beryl and simply log off and then back on again??

If it is a potential solution, could I add a script to the DVD playback icon (in my case VLC) that will point to the code to turn off Beryl and then autotically jump into VLC? 

I wish I could have multiple VLC players all at once, being opaque and with different films on, now that would be totally cool.

or is it somehow related to my video card (or rather lack of one!)

Dave

As it is I love the effects that Beryl have,

---

