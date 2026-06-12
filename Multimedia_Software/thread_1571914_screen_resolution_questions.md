---
title: "screen resolution questions"
date: 2010-09-10
forum: Multimedia Software
---

### Post by Chuck_N on 2010-09-10
hi,  I installed Ubuntu 10-04 LL on an old Dell laptop Latitude, driving a Dell 20-inch monitor.
Resolution now is  1280 x 1024. I've tried _some_ of the other resolutions and not had much luck,
they scramble the screen.  Problem is, although the screen is completely covered, and looks good,
when I look at pictures of people for example, they're all fat, cuz they're stretched to fit the screen width.
The picture of earth in my background Cosmos is stretched to fit the screen; shows as a big oval. That
I  can live with....   But how do I get pictures in F-SPOT or ImageViewer  to present accurately on the screen, and not be stretched to the sides?

-Chuck

---

### Post by aeiah on 2010-09-10
you'll find it best to tackle this problem by correcting your resolution to the one your monitor natively supports. i doubt its possible to alter the aspect ratio in f-spot etc, so setting the correct resolution is really all you can do.

is this monitor an LCD/TFT one or CRT? what is your graphics card?


if you dont know the specs of your graphics card, search for it in the output of:
```

sudo lshw

```

and post it here, or post the whole lot and someone will spot it for you.

---

### Post by Chuck_N on 2010-09-10
> **aeiah said:**
> [COLOR=Red]you'll find it best to tackle this problem by correcting your resolution to the one your monitor natively supports. i doubt its possible to alter the aspect ratio in f-spot etc, so setting the correct resolution is really all you can do.

is this monitor an LCD/TFT one or CRT? what is your graphics card?[/COLOR] [COLOR=Red]

if you dont know the specs of your graphics card, search for it in the output of:[/COLOR]  [COLOR=Red]
```

sudo lshw

```and post it here, or post the whole lot and someone will spot it for you[/COLOR].


okay..........here it is.............

 ```

chuck-laptop              
    description: Portable Computer
    product: Latitude C640
    vendor: Dell Computer Corporation
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-0000-1000-8000-80C04F000000
  *-core
       description: Motherboard
       vendor: Dell Computer Corporation
       physical id: 0
       serial: .       .              .
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A10 (01/12/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect pcmciaboot int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.7
          slot: Microprocessor
          size: 1200MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 640MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 128MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-ebffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:c000(size=4096) memory:fc000000-fdffffff memory:e0000000-e7ffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: Radeon Mobility M7 LW [Radeon Mobility 7500]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master vga_palette cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:11 memory:e0000000-e7ffffff(prefetchable) ioport:c000(size=256) memory:fcff0000-fcffffff memory:fc000000-fc01ffff(prefetchable)
        *-usb
             description: USB Controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf80(size=32)
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:e000(size=8192) memory:f4000000-fbffffff memory:28000000-31ffffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 78
                serial: 00:0b:db:a4:c9:8a
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.100 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
                resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:30000000-3001ffff(prefetchable)
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1420 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:f8000000-f8000fff ioport:e000(size=256) ioport:e400(size=256) memory:28000000-2bffffff(prefetchable) memory:f4000000-f7ffffff
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1420 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:f8001000-f8001fff ioport:e800(size=256) ioport:f000(size=256) memory:2c000000-2fffffff(prefetchable) memory:34000000-37ffffff
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
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
             product: 82801CAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:32000000-320003ff
           *-disk
                description: ATA Disk
                product: IC25N030ATMR04-0
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MOAO
                serial: MRG2E9KBDSVB3J
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000d672a
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 1e186bfb-8c31-4bc1-8274-846a7cb65591
                   size: 26GiB
                   capacity: 26GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2004-01-12 12:32:47 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;&#65533;&#65533;J&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;l&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1973;h &#65533;&#65533;h/&#65533;&#65533;&#65533;&#65533;&#1966;!&#65533;`N&#65533;`N&#28693;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1968;&#65533;&#65533;&#65533;]k modified=2010-09-06 06:17:34 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-09-10 06:24:19 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1224MiB
                   capacity: 1224MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1224MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CDRW/DVD SN-308B
                vendor: SAMSUNG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: U003
                serial: [SAMSUNG CDRW/DVD SN-308BU0030916U0030100
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: irq:5 ioport:d800(size=256) ioport:dc80(size=64)
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:d400(size=256) ioport:dc00(size=128)
  *-battery
       product: LIP8120DLP
       vendor: Sony Corp.
       physical id: 1
       slot: Left Module Bay
       capacity: 65120mWh
       configuration: voltage=14.8V
chuck@chuck-laptop:~$
```

---

### Post by realzippy on 2010-09-10
**Radeon Mobility M7 LW [Radeon Mobility 7500**

btw,if identifying graphicscard only better run:

```
lspci | grep VGA
```

What is monitors native resolution?
Which model is it?

---

### Post by Chuck_N on 2010-09-10
chuck@chuck-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
chuck@chuck-laptop:~$ 

okay, there's the shorter version.



The Dell monitor is  ST2010B
perhaps this is what you are looking for:

[IMG]http://i.dell.com/images/global/general/spacer.gif[/IMG] The Dell ST2010-BLK flat                                 panel monitor delivers.
[LIST]
[*]HD 1600 X 900 resolution
[*]16:9 aspect ratio great for watching movies on your PC
[*]5 millisecond response time (typical) for minimal ghosting
[*]1000:1 contrast ratio (typical)
[/LIST]

---

### Post by realzippy on 2010-09-10
1600 X 900 seems to be your desired resolution.
Do you have a file:

/etc/X11/xorg.conf   ?

If so,please post that file...

---

### Post by Chuck_N on 2010-09-10
[COLOR=Red]> **realzippy said:**
> 1600 X 900 seems to be your desired resolution.
Do you have a file:

/etc/X11/xorg.conf   ?[/COLOR]> **realzippy said:**
>  [COLOR=Red]

If so,please post that file...[/COLOR] 

this is what I got in Terminal

chuck@chuck-laptop:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: No such file or directory
chuck@chuck-laptop:~$ 

?? did I do it right ??

---

### Post by realzippy on 2010-09-10
No,this was the path to the file (if exists)...

```
gedit /etc/X11/xorg.conf
```

opens the file write-protected...,but you do not have that file (if,error would have been "permission denied")

---

### Post by realzippy on 2010-09-10
Can you confirm: no /etc/X11/xorg.conf file existing?

---

### Post by Chuck_N on 2010-09-10
chuck@chuck-laptop:~$ gedit /etc/X11/xorg.conf

opened a new blank gedit window named

xorg.conf   (/etc/X11) - gedit

---

### Post by realzippy on 2010-09-10
Yep,don`t have it,what is quite normal,since 10.04 uses KMS (KernelModeSetting) which makes xorg.conf obsolete.
If you would create such a file,it would be read,and a modeline for
your 1600x900 could be added.I suggest to test a few things with *xrandr*.
Can you post output from:

```
xrandr
```

---

### Post by Chuck_N on 2010-09-10
here you go..........

chuck@chuck-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900       60.0 +   60.0  
   1280x1024      75.0*    60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1400x1050      60.5 +   60.0  
   1600x1024      60.2  
   1280x1024      59.9     60.0  
   1440x900       59.9  
   1280x960       60.0     59.9  
   1280x854       59.9  
   1360x768       59.8  
   1280x800       59.8  
   1152x864       60.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)
chuck@chuck-laptop:~$

---

### Post by realzippy on 2010-09-10
Both screens are running (Laptop and extern) ?

---

### Post by Chuck_N on 2010-09-10
[COLOR=Red]> **realzippy said:**
> Both screens are running (Laptop and extern) ?[/COLOR]

no, I did not want laptop screen running 
I went to monitor preferences and turned laptop off.
When I take laptop out to use alone, I would enable it's monitor.

When I boot up the laptop monitor is on for a while, then the external  monitor 
comes on and the laptop goes away.....

Related (small) problem; I'd like to close the laptop cover once booted
but couldn't figure out how to get that done; right now I have to keep the cover
about 1/4 opened, to keep things going.  It's between me and my monitor, but not 
really in the way  1/4 open.

---

### Post by realzippy on 2010-09-10
please run:

```
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```

and after this run again:

```
xrandr
```

and post output (again)

---

### Post by Chuck_N on 2010-09-10
[COLOR=Red]> **realzippy said:**
> please run:

```
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```and after this run again:[/COLOR]> **realzippy said:**
>  [COLOR=Red]

```
xrandr
```and post output (again)[/COLOR] 

okay, I think it got in there; it gave me no indication of response.

the new  xrandr:

chuck@chuck-laptop:~$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
chuck@chuck-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900       60.0 +   60.0  
   1280x1024      75.0*    60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1400x1050      60.5 +   60.0  
   1600x1024      60.2  
   1280x1024      59.9     60.0  
   1440x900       59.9  
   1280x960       60.0     59.9  
   1280x854       59.9  
   1360x768       59.8  
   1280x800       59.8  
   1152x864       60.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)
  1600x900_60.00 (0x15a)  118.0MHz
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock   55.9KHz
        v: height  900 start  903 end  908 total  934           clock   59.8Hz
chuck@chuck-laptop:~$

---

### Post by realzippy on 2010-09-10
This added the mode to s-video....
Do you use an s-video cable to your extern monitor????



EDIT:
Ignore this post because
s-video is disconnected.I am confused about your external monitor being LVDS or VGA-0;assuming it is VGA-0 : post #18

---

### Post by realzippy on 2010-09-10
Run:

```
xrandr --newmode VGA-0 "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```

```
xrandr --addmode VGA-0  "1600x900_60.00"
```



and post ```
xrandr
``` output again...

---

### Post by Chuck_N on 2010-09-10
I don't think my old Latitude has s-video
but not sure.

I am connected with a blue (VGA?) cable, old style, with
the two connectors, one on each side of the 15?-pin plugin.

---

### Post by perspectoff on 2010-09-10
I could never get my Integrated Intel graphics to do higher resolutions properly until I tried this solution, which installs the old Intel graphics drivers (used in older versions of Ubuntu):

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I haven't tried this in Lucid, because I only use 1024x768 resolution and I have no problem with 1024x768 in Lucid. BTW, as I indicated in another thread, I am using the 845GV motherboard with Intel integrated graphics, as I believe you are.

---

### Post by realzippy on 2010-09-10
> **Chuck_N said:**
> I don't think my old Latitude has s-video
but not sure.

I am connected with a blue (VGA?) cable, old style, with
the two connectors, one on each side of the 15?-pin plugin.



ok,so please run commands given in post #18

---

### Post by realzippy on 2010-09-10
> **perspectoff said:**
> I could never get my Integrated Intel graphics to do higher resolutions properly until I tried this solution, which installs the old Intel graphics drivers (used in older versions of Ubuntu):

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I haven't tried this in Lucid, because I only use 1024x768 resolution and I have no problem with 1024x768 in Lucid. BTW, as I indicated in another thread, I am using the 845GV motherboard with Intel integrated graphics, as I believe you are.


...no,it's an ATI here...

---

### Post by realzippy on 2010-09-10
@ chuck: please run commands given in post #18 ...

---

### Post by Chuck_N on 2010-09-10
HELP
I did screen #18   First cmd worked fine.
second command as soon as I entered
screen got scrambled  3 zones of horizontal mess
monitor on laptop is on and has a similar but different pattern

I am now on my wife's computer
which she is not too happy about.

---

### Post by Chuck_N on 2010-09-10
I just got your personal message.........

sure hope the message I posted 11 min. ago is viewable by you

my computer is froze and I've done nothing to it since step 2 on window #18

---

### Post by realzippy on 2010-09-10
the commands are only temporarely,so just reboot...

---

### Post by Chuck_N on 2010-09-10
that's what I was hoping.....

I'll have to power-off, right ?

---

### Post by realzippy on 2010-09-10
yes

---

### Post by Chuck_N on 2010-09-10
phewwww
I'm operating again

any idea what went wrong?

do you see any mistake in the entries in #18?

---

### Post by realzippy on 2010-09-10
...the command does not set anything,it just adds an available resolution.
So I am surprised...maybe external monitor is not VGA-0 but LVDS.
Try:



```
xrandr --newmode LVDS "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```

then:

```
xrandr --addmode LVDS  "1600x900_60.00"
```

...if same disaster,reboot/power off.

---

### Post by Chuck_N on 2010-09-10
not good
but did not blow up

here is response from second command

chuck@chuck-laptop:~$ xrandr --addmode VGA-0  "1600x900_60.00"
xrandr: cannot find mode "1600x900_60.00"
chuck@chuck-laptop:~$

---

### Post by realzippy on 2010-09-10
Thats good...and what does

```
xrandr
```

show now?


Btw,hope you are not scared...and have a little patience?
We will not break anything....

---

### Post by realzippy on 2010-09-10
> **Chuck_N said:**
> not good
but did not blow up

here is response from second command

chuck@chuck-laptop:~$ xrandr --addmode [COLOR="Red"]VGA-0[/COLOR]  "1600x900_60.00"
xrandr: cannot find mode "1600x900_60.00"
chuck@chuck-laptop:~$

should be LVDS, of course;my mistake;edited the post 2 seconds after 
seing it,thats why there is no "edit" remark..

---

### Post by Chuck_N on 2010-09-10
xrandr:

chuck@chuck-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900       60.0 +   60.0  
   1280x1024      75.0*    60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1400x1050      60.5 +   60.0  
   1600x1024      60.2  
   1280x1024      59.9     60.0  
   1440x900       59.9  
   1280x960       60.0     59.9  
   1280x854       59.9  
   1360x768       59.8  
   1280x800       59.8  
   1152x864       60.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)
chuck@chuck-laptop:~$

---

### Post by realzippy on 2010-09-10
Ok,think we need a little break here an then have a new start.I am
now not sure (because of my confused posting/editing commands;sorry)if
you ran the command with *VGA-0* or *LVDS*,and I do not know if you formerly have run:
xrandr --newmode LVDS "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync.
I wonder why there is no freshly added mod in your xrandr output...
So,can you disconnect the external monitor and run

```
xrandr
```

again to know if internal display is VGA-0 or LVDS ?

---

### Post by Chuck_N on 2010-09-10
okay  I'll do that now

can vga plug be pulled from computer while running?

if you're leaving please suggest time you might be available......

---

### Post by realzippy on 2010-09-10
wrote pm..

Hot UnPlug VGA should work,but please reboot;promised that we won't break anything ;-)

---

### Post by Chuck_N on 2010-09-10
thanks.
I will reenable laptop monitor
then shut down
disconn vga
startup
submit xrandr
copy to reply
shutdown
reconnect vga
bootup
reset laptop monitor to off

---

### Post by Chuck_N on 2010-09-10
okay, here is the  xrandr   without the vga monitor

chuck@chuck-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 4096 x 4096
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1400x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1400x1050      60.5*+   60.0  
   1600x1024      60.2  
   1280x1024      59.9     60.0  
   1440x900       59.9  
   1280x960       60.0     59.9  
   1280x854       59.9  
   1360x768       59.8  
   1280x800       59.8  
   1152x864       60.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)
chuck@chuck-laptop:~$

---

### Post by realzippy on 2010-09-10
So,as assumed,VGA-0 is your extern monitor,As you can see in the xrandrs output (when connected)there is a mode 1600x900 for VGA-0:
1600x900 60.0 + 60.0

Problem is,I do not know about the "+ 60.0" in this mode,never have seen before.Seems as gnome's display manager -system/preferences/monitors- (which uses xrandr btw) also does not recognize this,or was there a resolution offered 1600x900
and just did not work ?

---

### Post by realzippy on 2010-09-10
Off course you could try it (and restart/power off if things go wrong)
and we see what happens when running existing 16/9 mode..this would be:

```
xrandr --output VGA-0 --mode 1600x900 60.0 + 60.0

```

---

### Post by Chuck_N on 2010-09-10
okay, I did  it.  Nothing happened.

Am I correct to be using  Applications/Accessories/Terminal
or should I be getting to Terminal "the other" way, which I forgot.

How am I supposed to get OUT of Terminal? 
I could not remember the command, had to  X  out.




But if I go to Display Settings and set to 1600X900 I get a scrambled screen and have to wait for restore.

---

### Post by Chuck_N on 2010-09-10
I tried all options under Display Settings.
I am on 1280X1024

if I switch to 1600X900 it scrambles
but wait and it restores

if I switch to 1152X864 it works BUT when I restore to 1280
  it scrambled and I had to power-down

if I try 1024X768 it works  
  but restore to 1280 and it scrambles & have to power-down

if I try 800X600 all is OK  Restore is OK

if I try 720  all is OK  Restore is OK.

---

### Post by realzippy on 2010-09-10
[I]Am I correct to be using Applications/Accessories/Terminal
or should I be getting to Terminal "the other" way, which I forgot.
How am I supposed to get OUT of Terminal? [/I]

Yes,you a correct by Applications/Accessories/Terminal
To *exit*terminal :
```
exit
```
or close the window.

*But if I go to Display Settings and set to 1600X900 I get a scrambled screen and have to wait for restore.*

So there is this 16/9 option,according to your xrandr output:
1600x900 60.0 + 60.0
....but not working.Strange that when running:
xrandr --output VGA-0 --mode 1600x900 60.0 + 60.0
nothing happens,it should get scrambled too.

I would like to run another test:
```

xrandr --output LVDS --off
```
then
```
xrandr --delmode VGA-0  "1600x900"
```
if error
```
xrandr --delmode VGA-0  "1600x900 60.0 + 60.0"
```
if error
```
xrandr --delmode VGA-0  "1600x900_60.0 + 60.0"
```
then
```
xrandr --newmode VGA-0 "1600x900"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```
then
```
xrandr --addmode VGA-0  "1600x900"
```
then finally  
```
xrandr --output VGA-0 --mode 1600x900

```

---

### Post by Chuck_N on 2010-09-10
okay, I'll get to work on that now.

I hope I'm not responsible for your missing the soccer game,
or whatever it was.

---

### Post by perspectoff on 2010-09-10
> **Chuck_N said:**
> chuck@chuck-laptop:~$ gedit /etc/X11/xorg.conf

opened a new blank gedit window named

xorg.conf   (/etc/X11) - gedit

HAL nowadays, not xorg.conf.

(Ah, the good old days of the PDP11 -- why don't they make computers like they used to?)

Perhaps use xorg.conf.failsafe ?

---

### Post by realzippy on 2010-09-10
> **perspectoff said:**
> HAL nowadays, not xorg.conf.

(Ah, the good old days of the PDP11 -- why don't they make computers like they used to?)

No.
KMS.HAL is for input devices from formerly xorg.conf e.g keyboard,mouse.
BTW,post [#11]("http://ubuntuforums.org/showpost.php?p=9829295&postcount=11")

*Perhaps use xorg.conf.failsafe ?*

Issue is that the native resolution 16/9 seems not to work,whether by xrandr nor display settings (which is the same afaik).
General idea is to create an xorg.conf with modeline 1600x900:.failsafe won't content this.
Wanted to find a mode with xrandr but unfortunately things do not behave as they should.

Could be good to have a "3rd eye" here,maybe you see what is going wrong here...

---

### Post by Chuck_N on 2010-09-10
I ran the code from frame #44 below,
I should have copied the results from Terminal and sent them to you
before executing the very last statement....

The last statement scrambled my screen and I could not get terminal to show
Had to poweroff.

should I do it all again?  No problem if you want to see it..............

---

### Post by realzippy on 2010-09-10
very last statement,means: xrandr --output VGA-0 --mode 1600x900 ?

BTW: Do you have any option in the monitor's menue  set to: "autoscan" "oversize" or
something like that???
Note that sometimes those options are pretty hidden in submenus..

---

### Post by Chuck_N on 2010-09-10
[COLOR=Red]> **realzippy said:**
> very last statement,means: xrandr --output VGA-0 --mode 1600x900 ?

BTW: Do you have any option in the monitor's menue  set to: "autoscan" "oversize" or[/COLOR][COLOR=Red]
something like that???
Note that sometimes those options are pretty hidden in submenus..[/COLOR][/QUOTE]

Yes, on submitting    
xrandr --output VGA-0 --mode 1600x900
 the screen scrambled.

Hidden or not, I don't have a clue where to look to see the monitor's menu.       8-(

The  MONITOR PREFERENCES  menu is extremely short aand simple; no option for oversize or autoscan

---

### Post by realzippy on 2010-09-10
Let me summarize (others might not read whole bunch):

[B]Issue is that the native resolution 16/9 seems not to work,whether by xrandr nor display settings.
10.04 uses KMS so there is no xorg.conf file;the ati (free) driver should work out of the box for VGA compatible controller Radeon Mobility 7500;seems it does,any other resolutions work,only external monitor's native refuses to.
My general idea was to create an xorg.conf file with modeline for 1600x900.
Generating such a modeline with xrandr fails;if it had worked we had to make this
permanent.[/B]
------


Maybe xrandr cannot set the size (xrandr--output aso,scrambled) because
your laptop's screen (LVDS) is screen1,which means we had to give a "virtual" screen size that is as large as both screens - what could be done: in the xorg.conf ...we do not have now. 
So we can run another test:

Delete the file monitors.xml (This file is created when running System/Preferences/Monitors ;so you get it back)

```
rm ~/.config/monitors.xml
```

and restart your laptop,so that laptop's screen is running and external monitor switched "on"
Do not go to System/Preferences/Monitors to switch it off or anything.Is the external monitor running then (showing same)?

---

### Post by realzippy on 2010-09-10
If external monitor running then (showing same)?

```
xrandr --output VGA-0 --mode 1280x1024 --left-of LVDS
```
then  
```
xrandr --output LVDS --off
```
then
```
xrandr --delmode VGA-0  "1600x900"
```
or
```
xrandr --delmode VGA-0  "1600x900 60.0 + 60.0"
``` 
or (whichever worked)
```
xrandr --delmode VGA-0  "1600x900_60.0 + 60.0"
```
then
```
xrandr --newmode VGA-0 "1600x900"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```
then
```
xrandr --addmode VGA-0  "1600x900"
```
then finally (scrambled again ?!)
```
xrandr --output VGA-0 --mode 1600x900
```


..if possible get all the outputs before crashing please 

..since it is midnight meanwhile,I might not respond anymore today;will continue tomorrow.This is a hard one  ;-)

---

### Post by Chuck_N on 2010-09-10
> **[COLOR=Red]realzippy said:**
> So we can run another test:

Delete the file monitors.xml (This file is created when running System/Preferences/Monitors ;so you get it back)[/COLOR] [/COLOR] [COLOR=Red]

```
rm ~/.config/monitors.xml
```and restart your laptop,so that laptop's screen is running and external monitor switched "on"[/COLOR] [COLOR=Red]
Do not go to System/Preferences/Monitors to switch it off or anything.Is the external monitor running then (showing same)?[/COLOR]

Delete the file monitors.xml (This file is created when running System/Preferences/Monitors)

Code:
---------
rm ~/.config/monitors.xml


[COLOR=Purple]I enabled the laptop screen. The two screens are showing identical stuff.
Now, before I do the _ rm _  would you maybe want to do a  RENAME  instead,
so that we can get it back if we need to ?

[/COLOR]
---------
and restart your laptop,so that laptop's screen is running.


Do not go to System/Preferences/Monitors to switch it off or anything.Is the external monitor running then (showing same)?

---

### Post by realzippy on 2010-09-11
[I]rm ~/.config/monitors.xml
... would you maybe want to do a RENAME instead,
so that we can get it back if we need to ?[/I]

When going to set up monitors with System/Preferences/Monitors this file is created easily,so I did not provide a backup.Off course you can rename it to backup;only
important thing is monitors.xml existing anymore when logging into gnome,since
monitor settings get loaded if exists;want a "vanilla" status before running the given commands;so ensure rebooting/logging out/in after deleting/moving/backupping that file...

Backup:
```
mv ~/.config/monitors.xml ~/.config/monitors.xml.backup
```

Restore:
```
mv ~/.config/monitors.xml.backup ~/.config/monitors.xml
```

---

### Post by Chuck_N on 2010-09-11
> **realzippy said:**
> [I]rm ~/.config/monitors.xml
... would you maybe want to do a RENAME instead,
so that we can get it back if we need to ?[/I]

When going to set up monitors with System/Preferences/Monitors this file is created easily,so I did not provide a backup.Off course you can rename it to backup;only
important thing is monitors.xml existing anymore when logging into gnome,since
monitor settings get loaded if exists;want a "vanilla" status before running the given commands;so ensure rebooting/logging out/in after deleting/moving/backupping that file...

Backup:
```
mv ~/.config/monitors.xml ~/.config/monitors.xml.backup
```Restore:
```
mv ~/.config/monitors.xml.backup ~/.config/monitors.xml
```


hi
I'm up, but not too awake yet

I did the  mv  instruction
mv ~/.config/monitors.xml ~/.config/monitors.xml.backup
now I'll send you this, then reboot and see what we have.
both monitors are on

---

### Post by Chuck_N on 2010-09-11
bootup went smooth.
both screens are showing as normal

---

### Post by realzippy on 2010-09-11
fine,
so you could start with the commands given in post # 52..

---

### Post by Chuck_N on 2010-09-11
the very first line of code

xrandr --output VGA-0 --mode 1280x1024 --left-of LVDS

scrambled both screens.
I waited a minute, then powered down.

---

### Post by realzippy on 2010-09-11
> **Chuck_N said:**
> the very first line of code

xrandr --output VGA-0 --mode 1280x1024 --left-of LVDS

scrambled both screens.
I waited a minute, then powered down.

Please try:

```
xrandr --output VGA-0 --mode 1024x768 --left-of LVDS
```

instead.

---

### Post by Chuck_N on 2010-09-11
[COLOR=Red]Please try:

[/COLOR]       [COLOR=Red]Code:[/COLOR]
     [COLOR=Red]xrandr --output VGA-0 --mode 1024x768 --left-of LVDS[/COLOR] 
[COLOR=Red]instead.


....[COLOR=Black]and then proceed through the rest of the steps, if possible ?


jeez, your last post took 23 minutes to appear in my inbox
[/COLOR][/COLOR]

---

### Post by Chuck_N on 2010-09-11
once again, immediate blowup

it looked different............ first black screen
  then a prettier scrambled screen

---

### Post by Chuck_N on 2010-09-11
If you want to add a mode with resolution 1024X768, you can enter the following command: (The output is shown following.)
 [INDENT]$ cvt 1024 768






I don't think we used   CVT  did we ?




Sample output
 [INDENT]# 1024×768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline &#8220;1024x768_60.00&#8243; 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
[/INDENT][/INDENT]

---

### Post by realzippy on 2010-09-11
Hello Chuck_N,
sorry for delay....had to wait til my GF fell asleep..  ;-)

[I]I don't think we used CVT did we ?
[/I]
We did.In post #15 I wanted you to run:
**xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync**
which should have added a modeline for your desired resolution (1600x900).This modeline was made on my machine,did not tell you,by the command
**cvt 1600 900**
With the command:
**xrandr**
I wanted to get overview about your available resolutions and the notations of your monitors,output was:
[I]chuck@chuck-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 443mm x 249mm
1600x900 60.0 + 60.0
1280x1024 75.0* 60.0
1152x864 75.0
1024x768 75.1 60.0
800x600 75.0 60.3
640x480 75.0 60.0
720x400 70.1
LVDS connected (normal left inverted right x axis y axis)
1400x1050 60.5 + 60.0
1600x1024 60.2
1280x1024 59.9 60.0
1440x900 59.9
1280x960 60.0 59.9
1280x854 59.9
1360x768 59.8
1280x800 59.8
1152x864 60.0
1280x720 59.9
1152x768 59.8
1024x768 60.0 59.9
800x600 60.3 59.9
848x480 59.7
720x480 59.7
640x480 59.9 59.4
S-video disconnected (normal left inverted right x axis y axis)
[/I]
VGA-0 is your external monitor,running ("*")  at 1280x1024 75.0* ,LVDS your laptop's,nothing running or wrong info ("*" is missed)
Note,post #58,command:
**xrandr --output VGA-0 --mode 1280x1024 --left-of LVDS**
scrambles the screen.....although it is this resolution VGA-0 can run;wanted to turn the monitor "virtually" to the left(**--left-of LVDS**) ,so that an eventually missing
Virtual Desktop Size when running:
**xrandr --output VGA-0 --mode 1600x900**
does not matter.
E.g.LVDS runs at 1024x768 and VGA-0 runs 1600x900,then the virtual desktop size should be about 2624x900.

[I]"Virtual Desktop Size
    This optional entry specifies the virtual screen resolution to be used. .... multiple of either 8 or 16 for most drivers, and a multiple of 32 when running in monochrome mode. The given value will be rounded down if this is not the case. [COLOR="Red"]Video modes which are too large for the specified virtual size will be rejected[/COLOR]. If this entry is not present, the virtual screen resolution will be set to accommodate all the valid video modes given in the Modes entry."[/I] 

We could do further tests with xrandr,e.g. modify the 1600x900 modeline by running cvt with 1600 900 59 instead of 1600 900 60,but when we continue
like we did,me giving commands and you sitting in front of a scrambled screen you might not be amused.Good that you had a look at *xrandr*.No need to worry,
test a few things you read,there will be no more harm than a reboot,nothing persists.
E.g. the command:
```
xrandr --output VGA-0 --set "scaling mode" "Full aspect"
```
should unstretch your extern monitor's screen (So you could see photos without fat people..).Does it work?

Back to concept,we need a xorg.conf file (remember,there is no more since 9.10,the kernel sets modes for the graphics driver,but if xorg.conf exists,it is dominant).
When vanilla xorg.conf is created,I want to add a few lines.
For this you have to stop the running X server.Write commands down.To stop X,you have to log out.Then at login screen press **Alt+Ctrl+F1** to drop to
shell,where you have to log in with your username/password.Then you stop running gnome session:
```
sudo service gdm stop
```
then run
```
sudo  Xorg -configure
```
Then
```
sudo reboot
```  

When back at gnome,you will find a file 
*xorg.conf.new* in your home directory.Backup this to your desktop to have it available for later editing:
```
cp /home/chuck/xorg.conf.new  /home/chuck/Desktop/xorg.conf.new
```
Then copy it to your X11 directory,so that it is loaded at next boot and we see if it works.Maybe we have to disable KMS,but we will see.:
```
sudo cp /home/chuck/xorg.conf.new  /etc/X11/xorg.conf
```
Then reboot to load it.
If next boot leads to scrambled or black screen,simply delete it:
```
sudo rm /etc/X11/xorg.conf
```
(can also be done from recovery mode,root shell,without "sudo")

Please post the *xorg.conf.new* you have created and tested.
Also post 
*/var/log/Xorg.0.log*
My time is extremely limtitated on sunday,maybe you have to wait for edited versions of the file until monday.

One last thing (I am not kidding);
Can you test another VGA-cable? (Assume your laptop has no dvi or hdmi output).Years ago there was a change in "EDID data channel",some pins changed.Month ago we had
a resolution problem here,after hours it turned out that a different vga-cable offered more resolutions on the same monitor...stumbled about cable related resolution issues in other threads also in the past,so please test it,it might save a lot of time (although it is kind of sport...)
Greetings
from Hamburg

---

### Post by Chuck_N on 2010-09-11
okay.........hi............. late night for you !!
I'll read the rest and set to work on it.

---

### Post by Chuck_N on 2010-09-11
xrandr --output VGA-0 --set "scaling mode" "Full aspect"

did not work

chuck@chuck-laptop:~$ xrandr --output VGA-0 --set "scaling mode" "Full aspect"
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  27
  Current serial number in output stream:  27
chuck@chuck-laptop:~$ 

I'll await your response to see what I should do next.  Looks like typeo ?

---

### Post by Chuck_N on 2010-09-11
I swapped cables with my wife's monitor.
Hers is heavier and white, but seems to work well on my monitor.

I hope my skinny black one will work for her,
when I hook it up.

I resubmitted the xrandr line
and got the same results:

chuck@chuck-laptop:~$ xrandr --output VGA-0 --set "scaling mode" "Full aspect"
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  27
  Current serial number in output stream:  27
chuck@chuck-laptop:~$

---

### Post by realzippy on 2010-09-12
*xrandr --output VGA-0 --set "scaling mode" "Full aspect"*

No typo,"scaling mode" and "full aspect" must be replaced with
e.g. 1024x768 and 1600x900  ;-) sorry was tired last night.Got this
from german xrandr wiki;unfortunately this does not work here.So forget it.

You got same results from:
```
xrandr
```
when using your wife's vga cable?
Or did you only try:
xrandr --output VGA-0 --set "scaling mode" "Full aspect" ?



Have you done the xorg.conf stuff?

Another question  (Can answer myself when you sent me the Xorg.0.log..):
Do you know the amount of video RAM your Radeon 7500 has?
.

---

### Post by Chuck_N on 2010-09-12
hi,
I only did    xrandr --output VGA-0 --set "scaling mode" "Full aspect  with her cable
and we've switched back cables.

Don't know  amount of video RAM my Radeon 7500 has

---

### Post by Chuck_N on 2010-09-12
I've read the  xorg.conf  stuff
there's steps in there I don't know how to do

I'm between a rock and a hard place for time

wife needs help and I've got things to do
b4 Tuesdays trip.

I'd best drop this now, for the sake of marital harmony

Thanks so much for your time and helpfulness; 
I'll hope to try this out again in a couple weeks.

If I can do anything for you, please let me know.........

sincerely, Chuck

---

