---
title: "Choppy Video Playback on all media"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by macpointman on 2007-04-21
Well here I am Loving Ubuntu and showing it off to everyone that I can.  Letting them know that there is a really cool alternative to Windows.  My Notebook is Microsoft free.  I figured that the best way to learn Linux was to just dive right into it.  So far things have been pretty good.

My new problem is this

I have choppy video when playing from hard drive and DVD.  I was doing a bit of research and blindly tried this.

[http://www.cs.cornell.edu/~djm/ubuntu/#fix-dma]("http://www.cs.cornell.edu/~djm/ubuntu/#fix-dma")

Now my DVD drive will not mount any DVDs funny thing is that it will mount CDs just fine.

If anyone can help that would be Awesome.
________________________
_Following is my 'fstab'_

```
[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=497d2201-353c-4feb-b325-1d833749c571 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
# UUID=07D6-0809  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4       /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=bc2c0dc1-5b0e-470e-8886-1ac5056ff5b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0[/I]
```
__________________________________
_Following is my 'hdparm.conf'_

```
[I]## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode
# --security-freeze Freeze the drive's security status
# security_freeze
# --security-unlock Unlock the drive's security
# security_unlock = PWD
# --security-set-pass Set security password
# security_pass = password
# --security-disable Disable drive locking
# security_disable
# --user-master Select password to use
# user-master = u
# --security-mode Set the security mode
# security_mode = h

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}
[/I]
```
_______________________________________
Thanks for any help you can give.

MacPointMan

---

### Post by Kobalt on 2007-04-22
About your video playback : did you install drivers for your graphic card ? Did you install DVD playback ([libdvdcss2]("http://ubuntuforums.org/showthread.php?t=413626&highlight=libdvdcss2")) ?

---

### Post by atze76 on 2007-04-23
I think that I have the same problem. I've got an ATI x700 and with kubuntu 6.06 + all the additional codecs, everything was fine. The problems with the video playback started with kubuntu 7.04 So it is definitely not a hardware perfomance issue.
First I installt the xorg fglrx driver from the ubuntu repository but for some reasons I couldn't make it work. So I installed the latest ATI driver (version 8.36.5) from ATI's homepage. The **fglrxinfo** command displays that the ATI driver is loaded and with glxgears I get around 3200 fps. It seems that at 3D acceleration is working fine.
But if I try to play a video, it doesn't matter which format (mpeg, mov, ts from the harddrive or a DVD from the DVD-drive) and it doesn't matter either which player I use (xine, kaffeine, mplayer), there are some noticable frame drops. I haven't measured it but I would say that video is rendered with less then 20 fps.

Any idea what could cause this problem?

---

### Post by atze76 on 2007-04-24
I found the following error message in /var/log/Xorg.0.log. I am not quite sure whether it shows the origin of the problem. If this AIGLX error leads to choppy videos, does anyone know how to fix this?

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

---

### Post by ubu-for on 2007-04-24
I've installed Feisty on my second PC with an AMD Athlon 1800 and an ATI Radeon 8500 card without any ATI drivers.  Videos and DVDs work just fine.

Enter this:

```
sudo hdparm /dev/hdc
```

Or this:

```
sudo hdparm /dev/dvd
```

My output:

```
/dev/dvd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
```

You only need libdvdcss2 for copy protected DVDs.

Maybe you could try VLC as alternative video player.

---

### Post by atze76 on 2007-04-24
ok, I tried to list the device setting. Unfortunately *feisty* (7.04) mapps all my drives (harddrive and DVD driver) to /dev/sdx. Basically as SATA devices. I think the problem is that for some reason the IO_support is set to 16-bit by default.
Then I tried to change it to 32-bit but hdparm is not able to do that. I get the error message:

[I] setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 IO_support   =  0 (default 16-bit)
[/I]

I assume that the choppy video playback comes from the 16-bit I/O setting. But no one seems to know a solution, how SATA device settings can be changed. Other people have the same problem as well. But they only complain that their HD transfer rate is low.

btw, I have also tried VLC but it's still the same. I have frame drops with VLC as well.

---

### Post by moon2js on 2007-05-02
Hi, I'm having choppy video, too. I've got an older machine (P3 with an ATI Radeon 7000) but video worked fine in Windows ME and XP many years ago.

I haven't tried a DVD yet, but I gather it would be choppy too.

Is this just an open source driver problem? This is a relatively fresh Feisty install, no messing with Xorg config yet.

I poked around Xorg logs and came up with this.

```
/var/log$ cat Xorg.0.log | grep "AIGLX"
(==) AIGLX enabled
(EE) AIGLX: **Screen 0 is not DRI capable**
```


Does it relate to the choppiness and is this something I can correct?

---

### Post by moon2js on 2007-05-02
So, I have another machine that used to run Edgy (video worked fine) and then I upgraded it to Feisty via the repos (and video continued to work fine).

But I just formatted and reinstalled Feisty from CD and now video is quite choppy.

Any ideas?

---

### Post by fakie_flip on 2007-05-02
> **moon2js said:**
> 
```
/var/log$ cat Xorg.0.log | grep "AIGLX"
(==) AIGLX enabled
(EE) AIGLX: **Screen 0 is not DRI capable**
```

This big long code is not necessary. Grep is able to search through text files without needing cat.

```
grep -i AIGLX /var/log/Xorg.0.log
```

Have a look at the grep man pages.

```
man grep
```

---

### Post by fakie_flip on 2007-05-02
> **moon2js said:**
> So, I have another machine that used to run Edgy (video worked fine) and then I upgraded it to Feisty via the repos (and video continued to work fine).

But I just formatted and reinstalled Feisty from CD and now video is quite choppy.

Any ideas?

You probably are missing libdvdcss2 and need it. You and the other guy both need to read here.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by moon2js on 2007-05-02
Thanks for the tip on grep. I don't use it regularly enough to remember how, but I'm trying to remedy that lately.

On one of my machines, I found out that disabling Desktop Effects got rid of the choppiness.

On the xubuntu machine, I'll try libdvdcss2, but I've never tried playing a DVD. I installed win32codecs and gstreamer stuff as per the "Enabling Multimedia in Feisty" sticky here in the forums. I'm using democracyplayer to download video for testing.

Does following the xine-y route in [help.ubuntu.com's RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") mess with the gstreamer stuff in Feisty? Or is it better?

When I first set up this computer, I set it up as a server with the server CD, but after adding xubuntu-desktop now I'm more or less using it as a secondary desktop. I'm wondering if the server kernel isn't quite right for multimedia hardware?

---

### Post by atze76 on 2007-05-02
I think something else must be wrong because libdvdcss2 is installed and I don't have the desktop effects enabled either.

---

### Post by bubbalouie on 2007-05-05
Hi,

I have been having troubles ith choppy video too, the following helped me solve the problem:

[http://ubuntuforums.org/showthread.php?t=432774&page=2&highlight=enable+direct+rendering]("http://ubuntuforums.org/showthread.php?t=432774&page=2&highlight=enable+direct+rendering")

I also enabled triple buffering (not sure if it was needed), I can't find thge link at the moment, but if necesary I can dig up my xorg.conf to show what is needed. I hope this helps.

Ryan

---

### Post by atze76 on 2007-05-05
unfortunately, glxinfo shows that direct rendering is enabled :-(
BTW, I use the latest ATI driver (8.36.5).

Any other ideas?

---

### Post by bubbalouie on 2007-05-05
A few, don't know if they'll help though, set your video to sync to vblank (video texture adapter and opengl), this needs to be done from the command line for ATI cards, off hand I don't remember the commands but it was fairly straight forward (ati-settings --help for info I think).

I have included my xorg.conf below, relevant sections in bold for the triple buffering. To be honest I did a quick test and on the same machine windows gives very slightly better performance for video playback, so I suspect I may too be missing something, though the direct rending and sync to vblank improved things a lot for me.

> 

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:39:38 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice     "Synaptics Touchpad"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7400"
[B]    Option 	   "RenderAccel"   "true"
    Option         "TripleBuffer" "true"[/B]
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x800 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection




---

### Post by fakie_flip on 2007-05-06
VertRefresh     0.0 - 60.0

That does not look good. You should put the correct values in there, and the same for this one.

HorizSync 29.0 - 49.0

Look up the specs for your monitor to know what they should be, and then change them.

---

### Post by bubbalouie on 2007-05-06
> **fakie_flip said:**
> VertRefresh     0.0 - 60.0

That does not look good. You should put the correct values in there, and the same for this one.

HorizSync 29.0 - 49.0

Look up the specs for your monitor to know what they should be, and then change them.

Sony Vaio VGN-FE25GP (laptop panel), I think the display is literally limited to 60hz so I never though much of it... any thoughts where i might find the right specs (google didn't find much)?

---

### Post by Teisei on 2007-05-06
I'm having similar problems with video choppiness. I recently installed a fresh copy of Feisty and I've installed all the proper media libraries. The choppiness occurs regardless of the media type but for me it only seems to be with HD video. I've installed the nvidia drivers.

---

### Post by atze76 on 2007-05-22
you should try to install the -386 kernel. That solved the problem for me. The 2.6.20-15-generic kernel seems to have some performance issues.

---

### Post by Kidge on 2007-05-31
how do u install kernels

---

