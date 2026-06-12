---
title: "Ubuntu resolution won't go higher than 800x600 - have tried everything"
date: 2009-07-19
forum: Multimedia Software
---

### Post by legalguy on 2009-07-19
Ubuntu resolution won't go higher than 800x600 - have tried everything

It's an old HP Pavillion xt963 motherboard with 1M video RAM.  I'm running
8.10 since it seems faster than jaunty.  It was running fine at 1024x768.  Then the VGA monitor
died and during troubleshooting I changed it to 800x600 and 1024x768 disappeared from the GUI.
Only 800x600 and 640x480 left in System > Prefs > Resolution.
Other settings:
System > Prefs > Appearance > Visual Effects = None
Trying to detect the monitor from the GUI has always been "Unknown"
Currently Viewsonic G90f straight to the MB, not going through a KVM.

BTW, everywhere I checked (including wiki.ubuntu.com/X/Config/Resolution#Resetting an out-of-range-resolution) never said if it was OK to work from a terminal in GNOME or it had to be from a failsafe terminal.  I tried some of both, didn't make a difference.
Things I've tried (not necessarily in this order, with a lot of reboots in between).

1.  rm /etc/X11/xorg.conf

2.  rebooting, picking recovery kernel and choosing xfix, resume

3.  dpkg-reconfigure -phigh xserver-xorg

4.  xrandr shows
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  

5.  cvt shows
root@fire-desktop:~# cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

6.  root@fire-desktop:~# xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  16 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

7.  root@fire-desktop:~# xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
  1024x768_60.00 (0x58)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz

8.  root@fire-desktop:~# xrandr --addmode VGA 1024x768
xrandr: cannot find output "VGA"

9.  root@fire-desktop:~# xrandr --addmode VGA-0 1024x768
xrandr: cannot find output "VGA-0"

10.  root@fire-desktop:~# xrandr --addmode 1024x768
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --off
      --crtc <crtc>
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>


11.  root@fire-desktop:~# xrandr --addmode VGA 1024x768
xrandr: cannot find output "VGA"

12.  root@fire-desktop:~# xrandr --addmode VGA-0 1024x768
xrandr: cannot find output "VGA-0"

13.  root@fire-desktop:~# xrandr --addmode 1024x768
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --off
      --crtc <crtc>
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>

13. xrandr --addmode 1024x768
..more of the same.

14. root@fire-desktop:~# xrandr --output --auto 
root@fire-desktop:~# 

15.  Here's the xorg.conf
root@fire-desktop:/etc/X11# more xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

I did not try to hand edit it, from what I read sound like that method was superceded long ago.

I'm stuck.

---

### Post by legalguy on 2009-07-19
additional info:

root@fire-desktop:~# lsmod
Module                  Size  Used by
i810                   25984  2 
drm                    86056  3 i810
af_packet              25728  4 
binfmt_misc            16904  1 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ipv6                  263972  14 
ppdev                  15620  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
wmi                    14504  0 
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
video                  25104  0 
output                 11008  1 video
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
wlan_scan_sta          20608  1 
ath_rate_sample        19968  1 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
parport_pc             39204  0 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_dummy          10884  0 
evdev                  17696  6 
ath_pci                99096  0 
container              11520  0 
wlan                  211952  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               198864  3 ath_rate_sample,ath_pci
snd_seq_oss            38528  0 
serio_raw              13444  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
psmouse                45200  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
pcspkr                 10624  0 
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
intel_agp              33724  1 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  3 drm,intel_agp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
ata_piix               24580  2 
uhci_hcd               30736  0 
libata                177312  3 pata_acpi,ata_generic,ata_piix
usbcore               148848  2 uhci_hcd
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
ne2k_pci               16480  0 
8390                   16768  1 ne2k_pci
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 


root@fire-desktop:~# lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Winbond Electronics Corp W89C940
01:09.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

root@fire-desktop:~# xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10502000
X.Org version: 1.5.2
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x400000b, revert to Parent
number of extensions:    31
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    Extended-Visual-Information
    GLX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RANDR
    RECORD
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XC-APPGROUP
    XC-MISC
    XFIXES
    XFree86-DGA
    XFree86-DRI
    XFree86-Misc
    XFree86-VidModeExtension
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    800x600 pixels (212x159 millimeters)
  resolution:    96x96 dots per inch
  depths (7):    16, 1, 4, 8, 15, 24, 32
  root window id:    0x4e
  depth of root window:    16 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    64
  preallocated pixels:    black 0, white 65535
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0xfa8033
    KeyPressMask             KeyReleaseMask           EnterWindowMask          
    LeaveWindowMask          ExposureMask             StructureNotifyMask      
    SubstructureNotifyMask   SubstructureRedirectMask FocusChangeMask          
    PropertyChangeMask       ColormapChangeMask       
  number of visuals:    3
  default visual id:  0x21
  visual:
    visual id:    0x21
    class:    TrueColor
    depth:    16 planes
    available colormap entries:    64 per subfield
    red, green, blue masks:    0xf800, 0x7e0, 0x1f
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x22
    class:    DirectColor
    depth:    16 planes
    available colormap entries:    64 per subfield
    red, green, blue masks:    0xf800, 0x7e0, 0x1f
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3c
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
root@fire-desktop:~#

---

### Post by utnubuuser on 2009-07-19
If you set a resolution inappropriate for your monitor in the Screen Resolution GUI tool, you can reset it by running rm ~/.config/monitors.xml from a terminal.

[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by legalguy on 2009-07-19
Tried it, didn't work.

I forgot to add I also tried logging out, then logging in again on the 'Run xclient script' session.  Didn't work.

Here's var/log/messages
Jul 19 16:24:09 fire-desktop -- MARK --
Jul 19 16:39:02 fire-desktop pulseaudio[5100]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jul 19 16:39:02 fire-desktop pulseaudio[5100]: main.c: This program is not intended to be run as root (unless --system is specified).
Jul 19 16:40:25 fire-desktop bonobo-activation-server (root-5257): could not associate with desktop session: Failed to connect to socket /tmp/dbus-9RYhZkRuLm: Connection refused
Jul 19 16:40:28 fire-desktop kernel: [ 2211.078888] [drm] DMA Cleanup
Jul 19 16:40:32 fire-desktop kernel: [ 2215.587287] mtrr: base(0xf8000000) is not aligned on a size(0x12c000) boundary
Jul 19 16:40:33 fire-desktop kernel: [ 2216.109209] [drm] Using v1.4 init.
Jul 19 16:40:33 fire-desktop kernel: [ 2216.111605] mtrr: base(0xf8000000) is not aligned on a size(0x3000000) boundary
Jul 19 16:41:50 fire-desktop kernel: [ 2293.381338] [drm] DMA Cleanup
Jul 19 16:41:53 fire-desktop kernel: [ 2296.384661] mtrr: base(0xf8000000) is not aligned on a size(0x12c000) boundary
Jul 19 16:41:54 fire-desktop kernel: [ 2296.906217] [drm] Using v1.4 init.
Jul 19 16:41:54 fire-desktop kernel: [ 2296.908741] mtrr: base(0xf8000000) is not aligned on a size(0x3000000) boundary
Jul 19 16:42:18 fire-desktop pulseaudio[5667]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jul 19 16:42:18 fire-desktop pulseaudio[5667]: main.c: This program is not intended to be run as root (unless --system is specified).
Jul 19 16:42:18 fire-desktop pulseaudio[5668]: pid.c: Stale PID file, overwriting.
Jul 19 16:43:00 fire-desktop bonobo-activation-server (root-5850): could not associate with desktop session: Failed to connect to socket /tmp/dbus-e6TpSbgI9t: Connection refused
Jul 19 16:43:01 fire-desktop kernel: [ 2364.450240] [drm] DMA Cleanup
Jul 19 16:43:03 fire-desktop kernel: [ 2366.431207] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 19 16:43:03 fire-desktop kernel: [ 2366.431224] apm: disabled on user request.
Jul 19 16:43:07 fire-desktop exiting on signal 15
Jul 19 16:45:15 fire-desktop syslogd 1.5.0#2ubuntu6: restart.
Jul 19 16:45:16 fire-desktop kernel: Inspecting /boot/System.map-2.6.27-14-generic
Jul 19 16:45:16 fire-desktop kernel: Cannot find map file.
Jul 19 16:45:16 fire-desktop kernel: Loaded 48395 symbols from 83 modules.
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Linux version 2.6.27-14-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Jun 30 19:57:39 UTC 2009 (Ubuntu 2.6.27-14.35-generic)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000000fef0000 (usable)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]  BIOS-e820: 000000000fef0000 - 000000000feffc00 (ACPI data)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]  BIOS-e820: 000000000feffc00 - 000000000ff00000 (ACPI NVS)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]  BIOS-e820: 000000000ff00000 - 0000000010000000 (reserved)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] DMI present.
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] last_pfn = 0xfef0 max_arch_pfn = 0x100000
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] RAMDISK: 0f70c000 - 0fedfe8a
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: RSDP 000F6EA0, 0014 (r0 PTLTD )
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: RSDT 0FEFC782, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: FACP 0FEFFB0A, 0074 (r1 HP     Hawk      6040000 PTL     F4240)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: DSDT 0FEFC7B2, 3358 (r1  INTEL  Whitney  6040000 MSFT  100000B)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: FACS 0FEFFFC0, 0040
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: APIC 0FEFFB7E, 005A (r1 PTLTD    APIC    6040000  LTP        0)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: BOOT 0FEFFBD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] 254MB LOWMEM available.
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   mapped low ram: 0 - 0fef0000
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   low ram: 00000000 - 0fef0000
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   bootmap 00012000 - 00013fe0
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fef0000]
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   #3 [0000100000 - 00005c39e0]    TEXT DATA BSS ==> [0000100000 - 00005c39e0]
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   #4 [000f70c000 - 000fedfe8a]          RAMDISK ==> [000f70c000 - 000fedfe8a]
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   #5 [00005c4000 - 00005c7000]    INIT_PG_TABLE ==> [00005c4000 - 00005c7000]
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   #8 [0000012000 - 0000014000]          BOOTMAP ==> [0000012000 - 0000014000]
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Zone PFN ranges:
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x0000fef0
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]   HighMem  0x0000fef0 -> 0x0000fef0
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul 19 16:45:16 fire-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0000fef0
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e7000
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e7000 - 0000000000100000
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff00000)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64577
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Kernel command line: root=UUID=70b4bee9-d1a4-4f56-bd3d-4ea004643ba2 ro quiet splash 
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Initializing CPU#0
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] TSC: using PMTIMER calibration value
Jul 19 16:45:16 fire-desktop kernel: [    0.000000] Detected 1202.721 MHz processor.
Jul 19 16:45:16 fire-desktop kernel: [    0.004000] Console: colour VGA+ 80x25
Jul 19 16:45:16 fire-desktop kernel: [    0.004000] console [tty0] enabled
Jul 19 16:45:16 fire-desktop kernel: [    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 19 16:45:16 fire-desktop kernel: [    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Jul 19 16:45:16 fire-desktop kernel: [    0.004000] Memory: 244996k/261056k available (2579k kernel code, 15492k reserved, 1162k data, 428k init, 0k highmem)
Jul 19 16:45:16 fire-desktop kernel: [    0.004000] virtual kernel memory layout:
Jul 19 16:45:16 fire-desktop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jul 19 16:45:16 fire-desktop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jul 19 16:45:16 fire-desktop kernel: [    0.004000]     vmalloc : 0xd0800000 - 0xff3fe000   ( 747 MB)
Jul 19 16:45:16 fire-desktop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xcfef0000   ( 254 MB)
Jul 19 16:45:16 fire-desktop kernel: [    0.004000]       .init : 0xc04ad000 - 0xc0518000   ( 428 kB)
Jul 19 16:45:16 fire-desktop kernel: [    0.004000]       .data : 0xc0384caa - 0xc04a7680   (1162 kB)
Jul 19 16:45:16 fire-desktop kernel: [    0.004000]       .text : 0xc0100000 - 0xc0384caa   (2579 kB)
Jul 19 16:45:16 fire-desktop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 19 16:45:16 fire-desktop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jul 19 16:45:16 fire-desktop kernel: [    0.004022] Calibrating delay loop (skipped), value calculated using timer frequency.. 2405.44 BogoMIPS (lpj=4810884)
Jul 19 16:45:16 fire-desktop kernel: [    0.004068] Security Framework initialized
Jul 19 16:45:16 fire-desktop kernel: [    0.004087] SELinux:  Disabled at boot.
Jul 19 16:45:16 fire-desktop kernel: [    0.004142] AppArmor: AppArmor initialized
Jul 19 16:45:16 fire-desktop kernel: [    0.004162] Mount-cache hash table entries: 512
Jul 19 16:45:16 fire-desktop kernel: [    0.004547] Initializing cgroup subsys ns
Jul 19 16:45:16 fire-desktop kernel: [    0.004558] Initializing cgroup subsys cpuacct
Jul 19 16:45:16 fire-desktop kernel: [    0.004564] Initializing cgroup subsys memory
Jul 19 16:45:16 fire-desktop kernel: [    0.004600] CPU: L1 I cache: 16K, L1 D cache: 16K
Jul 19 16:45:16 fire-desktop kernel: [    0.004607] CPU: L2 cache: 256K
Jul 19 16:45:16 fire-desktop kernel: [    0.004647] Checking 'hlt' instruction... OK.
Jul 19 16:45:16 fire-desktop kernel: [    0.020775] SMP alternatives: switching to UP code
Jul 19 16:45:16 fire-desktop kernel: [    0.028055] Freeing SMP alternatives: 11k freed
Jul 19 16:45:16 fire-desktop kernel: [    0.028064] ACPI: Core revision 20080609
Jul 19 16:45:16 fire-desktop kernel: [    0.029961] ACPI: Checking initramfs for custom DSDT
Jul 19 16:45:16 fire-desktop kernel: [    0.624073] ENABLING IO-APIC IRQs
Jul 19 16:45:16 fire-desktop kernel: [    0.624293] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 19 16:45:16 fire-desktop kernel: [    0.663989] CPU0: Intel(R) Celeron(TM) CPU                1200MHz stepping 01
Jul 19 16:45:16 fire-desktop kernel: [    0.664031] Brought up 1 CPUs
Jul 19 16:45:16 fire-desktop kernel: [    0.664031] Total of 1 processors activated (2405.44 BogoMIPS).
Jul 19 16:45:16 fire-desktop kernel: [    0.664031] net_namespace: 840 bytes
Jul 19 16:45:16 fire-desktop kernel: [    0.664031] Booting paravirtualized kernel on bare hardware
Jul 19 16:45:16 fire-desktop kernel: [    0.664031] Time: 16:44:43  Date: 07/19/09
Jul 19 16:45:16 fire-desktop kernel: [    0.664031] NET: Registered protocol family 16
Jul 19 16:45:16 fire-desktop kernel: [    0.664031] EISA bus registered
Jul 19 16:45:16 fire-desktop kernel: [    0.664031] ACPI: bus type pci registered
Jul 19 16:45:16 fire-desktop kernel: [    0.664031] PCI: PCI BIOS revision 2.10 entry at 0xfd99e, last bus=1
Jul 19 16:45:16 fire-desktop kernel: [    0.664031] PCI: Using configuration type 1 for base access
Jul 19 16:45:16 fire-desktop kernel: [    0.674637] ACPI: Interpreter enabled
Jul 19 16:45:16 fire-desktop kernel: [    0.674652] ACPI: (supports S0 S1 S5)
Jul 19 16:45:16 fire-desktop kernel: [    0.674675] ACPI: Using IOAPIC for interrupt routing
Jul 19 16:45:16 fire-desktop kernel: [    0.684520] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 19 16:45:16 fire-desktop kernel: [    0.684958] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Jul 19 16:45:16 fire-desktop kernel: [    0.684966] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
Jul 19 16:45:16 fire-desktop kernel: [    0.685467] pci 0000:00:1e.0: transparent bridge
Jul 19 16:45:16 fire-desktop kernel: [    0.689367] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Jul 19 16:45:16 fire-desktop kernel: [    0.689615] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Jul 19 16:45:16 fire-desktop kernel: [    0.689848] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jul 19 16:45:16 fire-desktop kernel: [    0.690085] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Jul 19 16:45:16 fire-desktop kernel: [    0.690503] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 19 16:45:16 fire-desktop kernel: [    0.690613] pnp: PnP ACPI init
Jul 19 16:45:16 fire-desktop kernel: [    0.690640] ACPI: bus type pnp registered
Jul 19 16:45:16 fire-desktop kernel: [    0.691878] pnp 00:01: io resource (0x1000-0x105f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
Jul 19 16:45:16 fire-desktop kernel: [    0.691889] pnp 00:01: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
Jul 19 16:45:16 fire-desktop kernel: [    0.697360] ACPI Error (dsopcode-0595): Field [ALB2] at 120 exceeds Buffer [CRSA] size 104 (bits) [20080609]
Jul 19 16:45:16 fire-desktop kernel: [    0.697378] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node cf01e3f0), AE_AML_BUFFER_LIMIT
Jul 19 16:45:16 fire-desktop kernel: [    0.697431] ACPI Error (uteval-0232): Method execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node cf01e3f0), AE_AML_BUFFER_LIMIT
Jul 19 16:45:16 fire-desktop kernel: [    0.700368] ACPI: ACPI bus type pnp unregistered
Jul 19 16:45:16 fire-desktop kernel: [    0.700379] PnPBIOS: Disabled by ACPI PNP
Jul 19 16:45:16 fire-desktop kernel: [    0.701362] PCI: Using ACPI for IRQ routing
Jul 19 16:45:16 fire-desktop kernel: [    0.701622] NET: Registered protocol family 8
Jul 19 16:45:16 fire-desktop kernel: [    0.701622] NET: Registered protocol family 20
Jul 19 16:45:16 fire-desktop kernel: [    0.701622] NetLabel: Initializing
Jul 19 16:45:16 fire-desktop kernel: [    0.701622] NetLabel:  domain hash size = 128
Jul 19 16:45:16 fire-desktop kernel: [    0.701622] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 19 16:45:16 fire-desktop kernel: [    0.701622] NetLabel:  unlabeled traffic allowed by default
Jul 19 16:45:16 fire-desktop kernel: [    0.701622] tracer: 772 pages allocated for 65536 entries of 48 bytes
Jul 19 16:45:16 fire-desktop kernel: [    0.701622]    actual entries 65620
Jul 19 16:45:16 fire-desktop kernel: [    0.701622] AppArmor: AppArmor Filesystem Enabled
Jul 19 16:45:16 fire-desktop kernel: [    0.701636] system 00:01: ioport range 0x1180-0x11bf has been reserved
Jul 19 16:45:16 fire-desktop kernel: [    0.701636] system 00:01: ioport range 0x1c00-0x1c7f has been reserved
Jul 19 16:45:16 fire-desktop kernel: [    0.701636] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jul 19 16:45:16 fire-desktop kernel: [    0.701636] system 00:01: ioport range 0x800-0x87f has been reserved
Jul 19 16:45:16 fire-desktop kernel: [    0.701636] system 00:01: ioport range 0xfe00-0xfe0f has been reserved
Jul 19 16:45:16 fire-desktop kernel: [    0.701636] system 00:01: iomem range 0xff800000-0xffffffff could not be reserved
Jul 19 16:45:16 fire-desktop kernel: [    0.739952] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
Jul 19 16:45:16 fire-desktop kernel: [    0.739964] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
Jul 19 16:45:16 fire-desktop kernel: [    0.739975] pci 0000:00:1e.0:   MEM window: 0xf4100000-0xf41fffff
Jul 19 16:45:16 fire-desktop kernel: [    0.739983] pci 0000:00:1e.0:   PREFETCH window: 0x00000020000000-0x000000200fffff
Jul 19 16:45:16 fire-desktop kernel: [    0.740035] bus: 00 index 0 io port: [0, ffff]
Jul 19 16:45:16 fire-desktop kernel: [    0.740039] bus: 00 index 1 mmio: [0, ffffffff]
Jul 19 16:45:16 fire-desktop kernel: [    0.740044] bus: 01 index 0 io port: [2000, 2fff]
Jul 19 16:45:16 fire-desktop kernel: [    0.740048] bus: 01 index 1 mmio: [f4100000, f41fffff]
Jul 19 16:45:16 fire-desktop kernel: [    0.740053] bus: 01 index 2 mmio: [20000000, 200fffff]
Jul 19 16:45:16 fire-desktop kernel: [    0.740057] bus: 01 index 3 io port: [0, ffff]
Jul 19 16:45:16 fire-desktop kernel: [    0.740061] bus: 01 index 4 mmio: [0, ffffffff]
Jul 19 16:45:16 fire-desktop kernel: [    0.740097] NET: Registered protocol family 2
Jul 19 16:45:16 fire-desktop kernel: [    0.740466] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
Jul 19 16:45:16 fire-desktop kernel: [    0.741032] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
Jul 19 16:45:16 fire-desktop kernel: [    0.741269] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jul 19 16:45:16 fire-desktop kernel: [    0.741488] TCP: Hash tables configured (established 8192 bind 8192)
Jul 19 16:45:16 fire-desktop kernel: [    0.741495] TCP reno registered
Jul 19 16:45:16 fire-desktop kernel: [    0.741815] NET: Registered protocol family 1
Jul 19 16:45:16 fire-desktop kernel: [    0.742179] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
Jul 19 16:45:16 fire-desktop kernel: [    1.329533]  it is
Jul 19 16:45:16 fire-desktop kernel: [    2.143824] Freeing initrd memory: 8015k freed
Jul 19 16:45:16 fire-desktop kernel: [    2.144611] Simple Boot Flag at 0x36 set to 0x1
Jul 19 16:45:16 fire-desktop kernel: [    2.146129] audit: initializing netlink socket (disabled)
Jul 19 16:45:16 fire-desktop kernel: [    2.146180] type=2000 audit(1248021884.144:1): initialized
Jul 19 16:45:16 fire-desktop kernel: [    2.157405] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul 19 16:45:16 fire-desktop kernel: [    2.163824] VFS: Disk quotas dquot_6.5.1
Jul 19 16:45:16 fire-desktop kernel: [    2.164862] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 19 16:45:16 fire-desktop kernel: [    2.165217] msgmni has been set to 494
Jul 19 16:45:16 fire-desktop kernel: [    2.165653] io scheduler noop registered
Jul 19 16:45:16 fire-desktop kernel: [    2.165661] io scheduler anticipatory registered
Jul 19 16:45:16 fire-desktop kernel: [    2.165666] io scheduler deadline registered
Jul 19 16:45:16 fire-desktop kernel: [    2.165715] io scheduler cfq registered (default)
Jul 19 16:45:16 fire-desktop kernel: [    2.166630] isapnp: Scanning for PnP cards...
Jul 19 16:45:16 fire-desktop kernel: [    2.520375] isapnp: No Plug & Play device found
Jul 19 16:45:16 fire-desktop kernel: [    2.667665] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jul 19 16:45:16 fire-desktop kernel: [    2.667902] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 19 16:45:16 fire-desktop kernel: [    2.668533] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jul 19 16:45:16 fire-desktop kernel: [    2.670430] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 19 16:45:16 fire-desktop kernel: [    2.671467] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jul 19 16:45:16 fire-desktop kernel: [    2.676578] brd: module loaded
Jul 19 16:45:16 fire-desktop kernel: [    2.676790] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 19 16:45:16 fire-desktop kernel: [    2.677150] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Jul 19 16:45:16 fire-desktop kernel: [    2.680387] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 19 16:45:16 fire-desktop kernel: [    2.680403] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 19 16:45:16 fire-desktop kernel: [    2.681709] mice: PS/2 mouse device common for all mice
Jul 19 16:45:16 fire-desktop kernel: [    2.682165] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Jul 19 16:45:16 fire-desktop kernel: [    2.682208] rtc0: alarms up to one month, y3k
Jul 19 16:45:16 fire-desktop kernel: [    2.682513] EISA: Probing bus 0 at eisa.0
Jul 19 16:45:16 fire-desktop kernel: [    2.682528] Cannot allocate resource for EISA slot 1
Jul 19 16:45:16 fire-desktop kernel: [    2.682534] Cannot allocate resource for EISA slot 2
Jul 19 16:45:16 fire-desktop kernel: [    2.682565] EISA: Detected 0 cards.
Jul 19 16:45:16 fire-desktop kernel: [    2.682575] cpuidle: using governor ladder
Jul 19 16:45:16 fire-desktop kernel: [    2.682580] cpuidle: using governor menu
Jul 19 16:45:16 fire-desktop kernel: [    2.683892] TCP cubic registered
Jul 19 16:45:16 fire-desktop kernel: [    2.683981] Using IPI No-Shortcut mode
Jul 19 16:45:16 fire-desktop kernel: [    2.684999] registered taskstats version 1
Jul 19 16:45:16 fire-desktop kernel: [    2.685223]   Magic number: 1:814:742
Jul 19 16:45:16 fire-desktop kernel: [    2.685607] rtc_cmos 00:04: setting system clock to 2009-07-19 16:44:45 UTC (1248021885)
Jul 19 16:45:16 fire-desktop kernel: [    2.685616] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 19 16:45:16 fire-desktop kernel: [    2.685622] EDD information not available.
Jul 19 16:45:16 fire-desktop kernel: [    2.687402] Freeing unused kernel memory: 428k freed
Jul 19 16:45:16 fire-desktop kernel: [    2.687535] Write protecting the kernel text: 2580k
Jul 19 16:45:16 fire-desktop kernel: [    2.687621] Write protecting the kernel read-only data: 940k
Jul 19 16:45:16 fire-desktop kernel: [    2.717312] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 19 16:45:16 fire-desktop kernel: [    3.212119] fuse init (API version 7.9)
Jul 19 16:45:16 fire-desktop kernel: [    3.465091] processor ACPI0007:00: registered as cooling_device0
Jul 19 16:45:16 fire-desktop kernel: [    4.228542] No dock devices found.
Jul 19 16:45:16 fire-desktop kernel: [    4.566517] SCSI subsystem initialized
Jul 19 16:45:16 fire-desktop kernel: [    4.746067] usbcore: registered new interface driver usbfs
Jul 19 16:45:16 fire-desktop kernel: [    4.746135] usbcore: registered new interface driver hub
Jul 19 16:45:16 fire-desktop kernel: [    4.768220] usbcore: registered new device driver usb
Jul 19 16:45:16 fire-desktop kernel: [    4.987757] USB Universal Host Controller Interface driver v3.0
Jul 19 16:45:16 fire-desktop kernel: [    4.994929] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jul 19 16:45:16 fire-desktop kernel: [    4.994965] uhci_hcd 0000:00:1f.2: UHCI Host Controller
Jul 19 16:45:16 fire-desktop kernel: [    4.995162] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
Jul 19 16:45:16 fire-desktop kernel: [    4.995230] uhci_hcd 0000:00:1f.2: irq 19, io base 0x00001080
Jul 19 16:45:16 fire-desktop kernel: [    4.995793] usb usb1: configuration #1 chosen from 1 choice
Jul 19 16:45:16 fire-desktop kernel: [    4.995866] hub 1-0:1.0: USB hub found
Jul 19 16:45:16 fire-desktop kernel: [    4.995892] hub 1-0:1.0: 2 ports detected
Jul 19 16:45:16 fire-desktop kernel: [    5.020448] Floppy drive(s): fd0 is 1.44M
Jul 19 16:45:16 fire-desktop kernel: [    5.039809] FDC 0 is a post-1991 82077
Jul 19 16:45:16 fire-desktop kernel: [    5.053629] ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
Jul 19 16:45:16 fire-desktop kernel: [    5.096948] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
Jul 19 16:45:16 fire-desktop kernel: [    5.098261] scsi0 : ata_piix
Jul 19 16:45:16 fire-desktop kernel: [    5.098717] scsi1 : ata_piix
Jul 19 16:45:16 fire-desktop kernel: [    5.098812] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0x10a0 irq 14
Jul 19 16:45:16 fire-desktop kernel: [    5.098818] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0x10a8 irq 15
Jul 19 16:45:16 fire-desktop kernel: [    5.263624] ata1.01: ATAPI: VOM-12E48X, VER-1008, max UDMA/33
Jul 19 16:45:16 fire-desktop kernel: [    5.268838] ata1.01: configured for UDMA/33
Jul 19 16:45:16 fire-desktop kernel: [    5.488444] ata2.00: ATA-6: ST380011A, 8.01, max UDMA/100
Jul 19 16:45:16 fire-desktop kernel: [    5.488455] ata2.00: 156301488 sectors, multi 16: LBA 
Jul 19 16:45:16 fire-desktop kernel: [    5.488485] ata2.00: limited to UDMA/33 due to 40-wire cable
Jul 19 16:45:16 fire-desktop kernel: [    5.504379] ata2.00: configured for UDMA/33
Jul 19 16:45:16 fire-desktop kernel: [    5.504928] scsi 0:0:1:0: CD-ROM                     VOM-12E48X       1008 PQ: 0 ANSI: 5
Jul 19 16:45:16 fire-desktop kernel: [    5.505340] scsi 1:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
Jul 19 16:45:16 fire-desktop kernel: [    5.505551] ne2k-pci 0000:01:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 19 16:45:16 fire-desktop kernel: [    5.506280] eth0: Winbond 89C940 found at 0x2000, IRQ 16, 00:20:78:18:5b:39.
Jul 19 16:45:16 fire-desktop kernel: [    6.923023] scsi 0:0:1:0: Attached scsi generic sg0 type 5
Jul 19 16:45:16 fire-desktop kernel: [    6.923120] scsi 1:0:0:0: Attached scsi generic sg1 type 0
Jul 19 16:45:16 fire-desktop kernel: [    6.990980] Driver 'sr' needs updating - please use bus_type methods
Jul 19 16:45:16 fire-desktop kernel: [    7.007409] sr0: scsi3-mmc drive: 47x/47x writer cd/rw xa/form2 cdda tray
Jul 19 16:45:16 fire-desktop kernel: [    7.007425] Uniform CD-ROM driver Revision: 3.20
Jul 19 16:45:16 fire-desktop kernel: [    7.009187] Driver 'sd' needs updating - please use bus_type methods
Jul 19 16:45:16 fire-desktop kernel: [    7.017297] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 19 16:45:16 fire-desktop kernel: [    7.017343] sd 1:0:0:0: [sda] Write Protect is off
Jul 19 16:45:16 fire-desktop kernel: [    7.017410] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 19 16:45:16 fire-desktop kernel: [    7.017632] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul 19 16:45:16 fire-desktop kernel: [    7.017666] sd 1:0:0:0: [sda] Write Protect is off
Jul 19 16:45:16 fire-desktop kernel: [    7.017730] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 19 16:45:16 fire-desktop kernel: [    7.017742]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
Jul 19 16:45:16 fire-desktop kernel: [    7.065580] sd 1:0:0:0: [sda] Attached SCSI disk
Jul 19 16:45:16 fire-desktop kernel: [    7.582416] PM: Starting manual resume from disk
Jul 19 16:45:16 fire-desktop kernel: [    7.663089] kjournald starting.  Commit interval 5 seconds
Jul 19 16:45:16 fire-desktop kernel: [    7.663145] EXT3-fs: mounted filesystem with ordered data mode.
Jul 19 16:45:16 fire-desktop kernel: [   15.070887] udevd version 124 started
Jul 19 16:45:16 fire-desktop kernel: [   16.934623] Linux agpgart interface v0.103
Jul 19 16:45:16 fire-desktop kernel: [   17.010880] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 19 16:45:16 fire-desktop kernel: [   17.055144] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 19 16:45:16 fire-desktop kernel: [   17.113138] iTCO_vendor_support: vendor-support=0
Jul 19 16:45:16 fire-desktop kernel: [   17.146586] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Jul 19 16:45:16 fire-desktop kernel: [   17.171844] iTCO_wdt: No card detected
Jul 19 16:45:16 fire-desktop kernel: [   17.292692] agpgart-intel 0000:00:00.0: Intel i810 Chipset
Jul 19 16:45:16 fire-desktop kernel: [   17.312030] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
Jul 19 16:45:16 fire-desktop kernel: [   17.312617] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 19 16:45:16 fire-desktop kernel: [   17.533871] intel_rng: FWH not detected
Jul 19 16:45:16 fire-desktop kernel: [   17.574308] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jul 19 16:45:16 fire-desktop kernel: [   17.584111] ACPI: Power Button (FF) [PWRF]
Jul 19 16:45:16 fire-desktop kernel: [   17.584548] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Jul 19 16:45:16 fire-desktop kernel: [   17.600055] ACPI: Power Button (CM) [PWRB]
Jul 19 16:45:16 fire-desktop kernel: [   18.720903] ath_hal: module license 'Proprietary' taints kernel.
Jul 19 16:45:16 fire-desktop kernel: [   18.843588] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Jul 19 16:45:16 fire-desktop kernel: [   19.435711] wlan: 0.9.4
Jul 19 16:45:16 fire-desktop kernel: [   19.570815] ath_pci: 0.9.4
Jul 19 16:45:16 fire-desktop kernel: [   19.572205] ath_pci 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 19 16:45:16 fire-desktop kernel: [   20.200328] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
Jul 19 16:45:16 fire-desktop kernel: [   21.462515] parport_pc 00:0b: disabled
Jul 19 16:45:16 fire-desktop kernel: [   21.464257] parport_pc: probe of 00:0b failed with error -22
Jul 19 16:45:16 fire-desktop kernel: [   21.712430] ath_rate_sample: 1.2 (0.9.4)
Jul 19 16:45:16 fire-desktop kernel: [   21.713752] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Jul 19 16:45:16 fire-desktop kernel: [   21.713769] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jul 19 16:45:16 fire-desktop kernel: [   21.713790] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jul 19 16:45:16 fire-desktop kernel: [   21.713804] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Jul 19 16:45:16 fire-desktop kernel: [   21.713813] wifi0: mac 7.9 phy 4.5 radio 5.6
Jul 19 16:45:16 fire-desktop kernel: [   21.713824] wifi0: Use hw queue 1 for WME_AC_BE traffic
Jul 19 16:45:16 fire-desktop kernel: [   21.713828] wifi0: Use hw queue 0 for WME_AC_BK traffic
Jul 19 16:45:16 fire-desktop kernel: [   21.713833] wifi0: Use hw queue 2 for WME_AC_VI traffic
Jul 19 16:45:16 fire-desktop kernel: [   21.713838] wifi0: Use hw queue 3 for WME_AC_VO traffic
Jul 19 16:45:16 fire-desktop kernel: [   21.713842] wifi0: Use hw queue 8 for CAB traffic
Jul 19 16:45:16 fire-desktop kernel: [   21.713846] wifi0: Use hw queue 9 for beacons
Jul 19 16:45:16 fire-desktop kernel: [   21.867918] wifi0: Atheros 5212: mem=0xf4100000, irq=17
Jul 19 16:45:16 fire-desktop kernel: [   21.869201] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 19 16:45:16 fire-desktop kernel: [   22.464098] intel8x0_measure_ac97_clock: measured 55473 usecs
Jul 19 16:45:16 fire-desktop kernel: [   22.464109] intel8x0: clocking to 48000
Jul 19 16:45:16 fire-desktop kernel: [   27.109856] lp: driver loaded but no devices found
Jul 19 16:45:16 fire-desktop kernel: [   27.428610] Adding 738948k swap on /dev/sda6.  Priority:-1 extents:1 across:738948k
Jul 19 16:45:16 fire-desktop kernel: [   28.087510] EXT3 FS on sda5, internal journal
Jul 19 16:45:16 fire-desktop kernel: [   29.587969] type=1505 audit(1248047112.778:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3743
Jul 19 16:45:16 fire-desktop kernel: [   30.092692] type=1505 audit(1248047113.286:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3748
Jul 19 16:45:16 fire-desktop kernel: [   30.093894] type=1505 audit(1248047113.286:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3748
Jul 19 16:45:16 fire-desktop kernel: [   30.327969] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 19 16:45:16 fire-desktop kernel: [   31.606124] ACPI: WMI: Mapper loaded
Jul 19 16:45:16 fire-desktop kernel: [   33.617845] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Jul 19 16:45:16 fire-desktop kernel: [   33.726095] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 19 16:45:16 fire-desktop kernel: [   33.726111] apm: overridden by ACPI.
Jul 19 16:45:17 fire-desktop kernel: [   34.015108] ppdev: user-space parallel port driver
Jul 19 16:45:17 fire-desktop kernel: [   34.258872] NET: Registered protocol family 10
Jul 19 16:45:17 fire-desktop kernel: [   34.263574] lo: Disabled Privacy Extensions
Jul 19 16:45:20 fire-desktop kernel: [   37.249052] cdrom: This disc doesn't have any tracks I recognize!
Jul 19 16:45:20 fire-desktop kernel: [   37.466813] Bluetooth: Core ver 2.13
Jul 19 16:45:20 fire-desktop kernel: [   37.471305] NET: Registered protocol family 31
Jul 19 16:45:20 fire-desktop kernel: [   37.471319] Bluetooth: HCI device and connection manager initialized
Jul 19 16:45:20 fire-desktop kernel: [   37.471331] Bluetooth: HCI socket layer initialized
Jul 19 16:45:20 fire-desktop kernel: [   37.516899] Bluetooth: L2CAP ver 2.11
Jul 19 16:45:20 fire-desktop kernel: [   37.516918] Bluetooth: L2CAP socket layer initialized
Jul 19 16:45:20 fire-desktop kernel: [   37.540995] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 19 16:45:20 fire-desktop kernel: [   37.541008] Bluetooth: BNEP filters: protocol multicast
Jul 19 16:45:20 fire-desktop kernel: [   37.571071] Bluetooth: RFCOMM socket layer initialized
Jul 19 16:45:20 fire-desktop kernel: [   37.571803] Bluetooth: RFCOMM TTY layer initialized
Jul 19 16:45:20 fire-desktop kernel: [   37.571822] Bluetooth: RFCOMM ver 1.10
Jul 19 16:45:20 fire-desktop kernel: [   37.625696] Bridge firewalling registered
Jul 19 16:45:20 fire-desktop kernel: [   37.656445] Bluetooth: SCO (Voice Link) ver 0.6
Jul 19 16:45:20 fire-desktop kernel: [   37.656459] Bluetooth: SCO socket layer initialized
Jul 19 16:45:25 fire-desktop kernel: [   41.984307] NET: Registered protocol family 17
Jul 19 16:45:26 fire-desktop kernel: [   43.425322] [drm] Initialized drm 1.1.0 20060810
Jul 19 16:45:26 fire-desktop kernel: [   43.444220] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 19 16:45:26 fire-desktop kernel: [   43.448895] [drm] Initialized i810 1.4.0 20030605 on minor 0
Jul 19 16:45:26 fire-desktop kernel: [   43.451207] mtrr: base(0xf8000000) is not aligned on a size(0x12c000) boundary
Jul 19 16:45:27 fire-desktop kernel: [   44.006243] [drm] Using v1.4 init.
Jul 19 16:45:27 fire-desktop kernel: [   44.008794] mtrr: base(0xf8000000) is not aligned on a size(0x3000000) boundary
Jul 19 16:46:05 fire-desktop pulseaudio[5021]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jul 19 16:46:05 fire-desktop pulseaudio[5021]: main.c: This program is not intended to be run as root (unless --system is specified).

---

### Post by trebory6 on 2009-07-20
I am having this same exact problem. Except mine just won't get to 1680x1050.

I have tried everything too, and nothing works.

---

### Post by legalguy on 2009-07-20
Yeah, I had this problem when it first installed too...I don't remember what it was that made it come up OK (chance?) but I remember the video was very blocky on the live CD, but going into appearance and switching desktop effects from normal to none fixed it up.

I'm pretty sure I could fix it by putting a better video card in it.  This 2001 mb only has pci 1x slots in it and I don't have any laying around.  I suppose I can ebay one of those.  I put it together out of scavenged parts so its cost to me was zero.

This one dual boots into XP, the XP works fine.

---

### Post by AKADAP on 2009-07-20
1 MB of video ram? What color depth are you running? at 800x600, best you could do is 16 bit color, 24 bit color would require 800x600x3 1.44 MB of video ram. best you could do at 1024x768 is 8 bit color.

---

### Post by legalguy on 2009-07-20
The color looked pretty good, maybe 16 bit or better?

The Phoenix BIOS 08/24/01  lets you choose between onboard or pci video, and video boot type 512K or 1M video ram (ram it takes from system ram, not video ram-I don't know if there is seperate video ram).  I had it set to onboard, 1MB.  Perhaps ubuntu can use more ram on its own initiative.

I also upgraded to Jaunty, made no difference.

Booting into windows xp, it shows 1152x864 pixesl of 24bit color.  Intel8281OE Graphics Controller into a Generic Monitor.

The slider did let me move it up to 1280x1024 but it froze up and had to reboot.

This did teach me one thing:  I used to dual boot all the time, but was messing around with virtualization (running win7 in virtualbox on jaunty), but from now on I'm always going to include an xp partition on every cptr. for troubleshooting if nothing else.  The 10Gigs it takes up is pretty trivial these days...

---

### Post by brookie on 2009-07-23
The only way I could get my display resolutions to show in the dropdown menu to show when I go to System/Preferences/Screen Resolution was to edit and customize my xorg.conf file to include the possible resolutions my card can support. 
Specifically I had to put them in the Section "Screen"/Subsection "Display"

Here is my xorg.conf file for dual monitors using my tv on S-video out. Just use it as a reference when setting up yours because it is specific to my system. See where I added my optional resolutions to my Subsection "Display" portion. 
I am running intrepid 8.10 on an inspiron 600m.
hope this may help.


Section "Monitor"
	Identifier      "laptop"
EndSection

Section "Monitor"
	Identifier	"SONY"
EndSection

Section "Screen"
	Identifier      "Default Screen"
	Monitor         "laptop"
	Device          "Radeon 9000"
	DefaultDepth    24
	SubSection "Display"
		Depth       24
		Modes       "1400x1050" "1280x1024" "1280x960" "1360x768" "1152x864" "1024x768" "800x600" "640x480"
		Virtual     2200 1050
	        #(virtual for 22in Visio(1680x1063) = 3080 1063, virtual for 32in Sony(800x600) = 2200 1050
	EndSubSection
EndSection

Section "Device"
	Identifier      "Radeon 9000"
	Driver          "ati"
	BusID           "PCI:1:0:0"
	Option          "monitor-LVDS"          "laptop"
	Option          "TVDACLoadDetect"       "TRUE"
	Option          "TVStandard"            "ntsc"
	Option          "monitor-S-video"       "SONY"
EndSection

---

### Post by cwsnyder on 2009-07-23
Since 7.10 (Gutsy Gibbon), my first Ubuntu version, I have had to use a custom /etc/X11/xorg.conf file because my Etronix 1701B LCD monitor is not properly detected.  Sounds like you need a similar file for your Viewsonic G90f crt monitor.

Try changing the following sections in your xorg.conf file to ```
Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Viewsonic"
Modelname "G90f"
Horizsync 31.5-97.0
Vertrefresh 56.0 - 180.0
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Virtual 1600 1200
Modes "1600x1200@77" "1280x1024@60" "1024x768@60" "1280x960@60" "800x600@60" "800x600@56" "640x480@60"
EndSubSection
EndSection

```.  You may or may not be able to use any of the modes beyond 1024x768, depending on your video card capabilities.  Remember that the **Depth 24** specifies a default color depth of 24 bits.  You may have to change that if you have only 1M of video memory.  

The **Section "Screen"** is supposed to describe your VIDEO CARD capabilities, not your actual monitor.  **Section "Monitor"** actually describes your monitor's capabilities.  At least to the best I have been able to determine.

---

### Post by legalguy on 2009-07-24
CWSNIDER fixed it...he's my new best friend

The settings as written in that code snippet actually kill the x server.  Past a certain point in the boot all you'll see is a black screen.

Booting in recovery mode allows you to drop to a root prompt.  I edited out all the higher modes than 1024x768 from both the screen and monitor sections, and changed the color depth to 16.  Resume normal boot and life is good.

It has some new behavior..it booted up to 1440x1050 at 60 hertz, and has a whole of lesser resolutions available too.  It seems clear that resolution is being set somewhere else...

Thanks everyone who tried to help...

---

