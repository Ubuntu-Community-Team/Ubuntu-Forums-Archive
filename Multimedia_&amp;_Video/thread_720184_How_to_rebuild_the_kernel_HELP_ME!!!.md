---
title: "How to rebuild the kernel? HELP ME!!!"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by ann pic on 2008-03-10
Now i am trying to install the driver of my new hardware (capture card), but it is still fail. I have try to install the driver and i notice that i need to rebuild my kernel. I am using ubuntu 7.10. I am a beginner in Linux and i have difficulities to rebuild the kernel. Got anyone out there can help me? I really need help. Here i attached the output error during the installation:-

ann@ann-desktop:~$ cd /home/ann
ann@ann-desktop:~$ ls
bttv Desktop motion-3.2.9.tar.gz Public
bttv-0.9.15 Documents Music Templates
bttv-0.9.15.tar.tar Examples Pictures Videos
ann@ann-desktop:~$ cd bttv
ann@ann-desktop:~/bttv$ ./configure
bash: ./configure: No such file or directory
ann@ann-desktop:~/bttv$ make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/ann/bttv-0.9.15 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
CC [M] /home/ann/bttv-0.9.15/video-buf.o
/home/ann/bttv-0.9.15/video-buf.c:46: error: expected ')' before string constant
make[2]: *** [/home/ann/bttv-0.9.15/video-buf.o] Error 1
make[1]: *** [_module_/home/ann/bttv-0.9.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
ann@ann-desktop:~/bttv$

---

### Post by kaens on 2008-03-10
Are you sure it's not in the kernel already? Their site says that it's included in the standard 2.6 kernels.

try seeing if 
```

$ lsmod | grep bttv

```

reports anything, and if not try

```

sudo modprobe bttv

```

I don't think you'll need to rebuild your kernel either way.

If it turns out you still need to make and install bttv, make sure you read the stuff in the doc directery of the source, particularly README.bttv and make sure your card is in CARDLIST.bttv.

---

### Post by ann pic on 2008-03-11
Hi Kaens, if i used lspci | grep Bt the output is as below.. Is it the bttv driver is already install?

ann@ann-desktop:~$ lspci | grep Bt
06:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
06:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
ann@ann-desktop:~$ cat /etc/modules.d/alsa
cat: /etc/modules.d/alsa: No such file or directory
ann@ann-desktop:~$ lsmod
Module Size Used by
ipv6 273892 10
nls_iso8859_1 5120 1
nls_cp437 6784 1
vfat 14080 1
fat 54300 1 vfat
af_packet 24840 2
i915 25856 2
drm 83348 3 i915
rfcomm 42136 2
l2cap 26240 11 rfcomm
bluetooth 57060 4 rfcomm,l2cap
uinput 10368 2
ppdev 10244 0
capifs 6792 1
snd_atiixp_modem 17160 0
snd_via82xx_modem 16264 0
snd_intel8x0m 18572 0
snd_ac97_codec 100644 3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
ac97_bus 3200 1 snd_ac97_codec
acpi_cpufreq 10568 0
cpufreq_conservative 8072 0
cpufreq_ondemand 9612 2
cpufreq_stats 7232 0
freq_table 5792 3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace 5280 0
cpufreq_powersave 2688 0
container 5504 0
ac 6148 0
video 18060 0
sbs 19592 0
button 8976 0
dock 10656 0
battery 11012 0
sbp2 24072 0
parport_pc 37412 0
lp 12580 0
parport 37448 3 ppdev,parport_pc,lp
snd_hda_intel 263712 1
snd_pcm_oss 44672 0
snd_mixer_oss 17664 1 snd_pcm_oss
snd_pcm 80388 6
snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_pcm_oss
snd_seq_dummy 4740 0
snd_seq_oss 33152 0
bttv 177012 0
video_buf 26244 1 bttv
ir_common 35460 1 bttv
snd_seq_midi 9600 0
compat_ioctl32 2304 1 bttv
snd_rawmidi 25728 1 snd_seq_midi
i2c_algo_bit 7428 1 bttv
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
btcx_risc 5896 1 bttv
snd_seq 53232 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tveeprom 16784 1 bttv
i2c_core 26112 3 bttv,i2c_algo_bit,tveeprom
snd_timer 24324 2 snd_pcm,snd_seq
snd_seq_device 9228 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev 29312 1 bttv
v4l2_common 18432 2 bttv,videodev
sr_mod 17828 0
cdrom 37536 1 sr_mod
pcspkr 4224 0
serio_raw 8068 0
psmouse 39952 0
v4l1_compat 15364 2 bttv,videodev
snd 54660 15
snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_pcm_oss,
snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 8800 1 snd
snd_page_alloc 11400 5
snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
e1000_ich9 188736 0
intel_agp 25620 1
heci 59916 0
shpchp 34580 0
pci_hotplug 32704 1 shpchp
agpgart 35016 3 drm,intel_agp
evdev 11136 7
ext3 133896 1
jbd 60456 1 ext3
mbcache 9732 1 ext3
usbhid 29536 0
hid 28928 1 usbhid
sg 36764 0
sd_mod 30336 8
ata_generic 8452 0
usb_storage 73024 1
ide_core 116804 1 usb_storage
libusual 18448 1 usb_storage
ohci1394 36528 0
pata_marvell 8064 0
ieee1394 96312 2 sbp2,ohci1394
ata_piix 17540 5
libata 125168 3 ata_generic,pata_marvell,ata_piix
scsi_mod 147084 6 sbp2,sr_mod,sg,sd_mod,usb_storage,libata
ehci_hcd 36492 0
uhci_hcd 26640 0
usbcore 138632 6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal 14344 0
processor 32072 2 acpi_cpufreq,thermal
fan 5764 0
fuse 47124 7
apparmor 40728 0
commoncap 8320 1 apparmor
ann@ann-desktop:~$ dmesg | grep Bt
[ 11.180000] bttv: Bt8xx card found (0).
[ 11.180000] bttv0: Bt878 (rev 17) at 0000:06:00.0, irq: 20, latency: 32, mmio: 0x50001000
ann@ann-desktop:~$ modprobe pal=i debug =1
FATAL: Module pal=i not found.
ann@ann-desktop:~$



My hardwares:-
Actually my multimedia video controller is detected but, i am not sure if the bttv driver is installed. Is it if my hardware is detected, the driver is already installed?

ann@ann-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics
Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller (rev
02)
00:19.0 Ethernet controller: Intel Corporation 82801I (ICH9 Family) Gigabit Ethernet Controller (rev
02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller
(rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev
b1)
06:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
06:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller
(PHY/Link)
ann@ann-desktop:~$ cat /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 15
model name : Intel(R) Core(TM)2 Duo CPU E6550 @ 2.33GHz
stepping : 11
cpu MHz : 1998.000
cache size : 4096 KB
physical id : 0
siblings : 2
core id : 0
cpu cores : 2
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts
acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx smx est tm2 ssse3 cx16
xtpr lahf_lm
bogomips : 4669.67
clflush size : 64
processor : 1
vendor_id : GenuineIntel
cpu family : 6
model : 15
model name : Intel(R) Core(TM)2 Duo CPU E6550 @ 2.33GHz
stepping : 11
cpu MHz : 1998.000
cache size : 4096 KB
physical id : 0
siblings : 2
core id : 1
cpu cores : 2
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts
acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx smx est tm2 ssse3 cx16
xtpr lahf_lm
bogomips : 4666.46
clflush size : 64
ann@ann-desktop:~$

---

### Post by kaens on 2008-03-11
The bttv module was reported by lsmod, which means that it's already installed.

lsmod lists the modules loaded into the kernel.

---

### Post by ann pic on 2008-03-12
But when i connect my capture card to analouge camera, seems like there is no image can be seen. Is it i need to install my camera analogue driver as well?

---

### Post by Whiffle on 2008-03-12
What program are you using?  It may not be setup right.  If the driver for your capture card is installed, that should be all the drivers you need.

---

### Post by ann pic on 2008-03-12
i am using motion software that i download from [www.zoneminder.com](www.zoneminder.com)
Once i install it i should can see the output from the camera, isn't?

---

### Post by Whiffle on 2008-03-12
Hmmm, I'm not familiar with that software but I'll do what I can.  In short, once the software and the driver are installed, it should work, in theory.  Chances are we've got some disconnect between the two and they aren't talking or theres some kind of permissions issue.  Lets start by checking to make sure all your hardware is present and accounted for:

Could you post the output of:
```
dmesg | grep bttv 
```

```
lspci | grep Bt878
```

```
xawtv -hwscan 
```

If you don't have that last one, you may have to install it, it should be available through Synaptic.


I actually have to go to bed pretty quickly now, but this is the howto i'm looking at:
[http://www.zoneminder.com/wiki/index.php/WinFast_TV2000_XP](http://www.zoneminder.com/wiki/index.php/WinFast_TV2000_XP)

---

### Post by ann pic on 2008-03-14
Hi Whiffle.. 

the outputs:

code: dmesg | grep bttv

ann@ann-desktop:~$ dmesg | grep bttv
[   10.568000] bttv: driver version 0.9.17 loaded
[   10.568000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   10.568000] bttv: Bt8xx card found (0).
[   10.568000] bttv0: Bt878 (rev 17) at 0000:06:00.0, irq: 20, latency: 32, mmio: 0x50001000
[   10.568000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   10.568000] bttv0: gpio: en=00000000, out=00000000 in=00f360ff [init]
[   23.368000] bttv0: using tuner=-1
[   23.368000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   29.768000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   36.168000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   42.568000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   48.968000] bttv0: registered device video0
[   48.968000] bttv0: registered device vbi0
ann@ann-desktop:~$ 


code: lspci | grep Bt878
06:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
06:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
ann@ann-desktop:~$ 

for xawtv, i have not install it yet..

So according to the output above, is it my driver already installed? Well, i am beginner. I am really run out of ideas because i only depends on forums to help me.

---

### Post by ann pic on 2008-03-14
i can find the xawtv through synaptic but it cannot simply installed by type sudo apt-get install command. It say that I need to enable the 'universe'. How i want to enable it?

---

### Post by Whiffle on 2008-03-14
Yep looks like your driver is installed.  This line tells us that:
```

[ 48.968000] bttv0: registered device video0
 [ 48.968000] bttv0: registered device vbi0

```

Heres some good information about the repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

There is a section there called "Adding the Universe and Multiverse Repositories", which is what you'll need to do to get xawtv.

---

### Post by ann pic on 2008-03-14
hi whiffle.. i already installed xawtv the output is as below..

ann@ann-desktop:~$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
looking for available devices
port 73-73
    type : Xvideo, image scaler
    name : Intel(R) Video Overlay

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video ( *** UNKNOWN/GENER
    flags: overlay capture tuner 

So now i think my analogue camera should be functioned once i connect to my BNC connector at capture card, am i rite?

---

### Post by Whiffle on 2008-03-14
I should think so, and theres some good info about your app on that link i posted earlier, which tells much more than I know.

---

### Post by ann pic on 2008-03-16
i want to run my xawtv and i exactly follow the instruction at 
[http://www.zoneminder.com/wiki/index...Fast_TV2000_XP](http://www.zoneminder.com/wiki/index...Fast_TV2000_XP) but i can't get same output as written in the web. am i missing something or any configuration?

ann@ann-desktop:~$ zmu d /dev/video0 q v
Extraneous options, d /dev/video0 q v 
zmu <-d device_path> [-v] [function] [-U<username> -P<password>]
zmu <-m monitor_id> [-v] [function] [-U<username> -P<password>]
General options:
  -h, --help                     : This screen
  -v, --verbose                  : Produce more verbose output
  -l, --list                     : List the current status of active (or all with -v) monitors
Options for use with devices:
  -d, --device <device_path>     : Get the current video device settings for <device_path>
  -q, --query                    : Query the current settings for the device
Options for use with monitors:
  -m, --monitor <monitor_id>     : Specify which monitor to address, default 1 if absent
  -q, --query                    : Query the current settings for the monitor
  -s, --state                    : Output the current monitor state, 0 = idle, 1 = prealarm, 2 = alarm,
                                   3 = alert, 4 = tape
  -B, --brightness [value]       : Output the current brightness, set to value if given 
  -C, --contrast [value]         : Output the current contrast, set to value if given 
  -H, --hue [value]              : Output the current hue, set to value if given 
  -O, --colour [value]           : Output the current colour, set to value if given 
  -i, --image [image_index]      : Write captured image to disk as <monitor_name>.jpg, last image captured
                                   or specified ring buffer index if given.
  -S, --scale <scale_%ge>        : With --image specify any scaling (in %) to be applied to the image
  -t, --timestamp [image_index]  : Output captured image timestamp, last image captured or specified
                                   ring buffer index if given
  -R, --read_index               : Output ring buffer read index
  -W, --write_index              : Output ring buffer write index
  -e, --event                    : Output last event index
  -f, --fps                      : Output last Frames Per Second captured reading
  -z, --zones                    : Write last captured image overlaid with zones to <monitor_name>-Zones.jpg
  -a, --alarm                    : Force alarm in monitor, this will trigger recording until cancelled with -c
  -n, --noalarm                  : Force no alarms in monitor, this will prevent alarms until cancelled with -c
  -c, --cancel                   : Cancel a forced alarm/noalarm in monitor, required after being enabled with -a or -n
  -L, --reload                   : Signal monitor to reload settings
  -E, --enable                   : Enable detection, wake monitor up
  -D, --disable                  : Disble detection, put monitor to sleep
  -u, --suspend                  : Suspend detection, useful to prevent bogus alarms when panning etc
  -r, --resume                   : Resume detection after a suspend
  -U, --username <username>      : When running in authenticated mode the username and
  -P, --password <password>      : password combination of the given user
  -A, --auth <authentication>    : Pass authentication hash string instead of user details
ann@ann-desktop:~$ zmu d /dev/video0 q v
Extraneous options, d /dev/video0 q v 
zmu <-d device_path> [-v] [function] [-U<username> -P<password>]
zmu <-m monitor_id> [-v] [function] [-U<username> -P<password>]
General options:
  -h, --help                     : This screen
  -v, --verbose                  : Produce more verbose output
  -l, --list                     : List the current status of active (or all with -v) monitors
Options for use with devices:
  -d, --device <device_path>     : Get the current video device settings for <device_path>
  -q, --query                    : Query the current settings for the device
Options for use with monitors:
  -m, --monitor <monitor_id>     : Specify which monitor to address, default 1 if absent
  -q, --query                    : Query the current settings for the monitor
  -s, --state                    : Output the current monitor state, 0 = idle, 1 = prealarm, 2 = alarm,
                                   3 = alert, 4 = tape
  -B, --brightness [value]       : Output the current brightness, set to value if given 
  -C, --contrast [value]         : Output the current contrast, set to value if given 
  -H, --hue [value]              : Output the current hue, set to value if given 
  -O, --colour [value]           : Output the current colour, set to value if given 
  -i, --image [image_index]      : Write captured image to disk as <monitor_name>.jpg, last image captured
                                   or specified ring buffer index if given.
  -S, --scale <scale_%ge>        : With --image specify any scaling (in %) to be applied to the image
  -t, --timestamp [image_index]  : Output captured image timestamp, last image captured or specified
                                   ring buffer index if given
  -R, --read_index               : Output ring buffer read index
  -W, --write_index              : Output ring buffer write index
  -e, --event                    : Output last event index
  -f, --fps                      : Output last Frames Per Second captured reading
  -z, --zones                    : Write last captured image overlaid with zones to <monitor_name>-Zones.jpg
  -a, --alarm                    : Force alarm in monitor, this will trigger recording until cancelled with -c
  -n, --noalarm                  : Force no alarms in monitor, this will prevent alarms until cancelled with -c
  -c, --cancel                   : Cancel a forced alarm/noalarm in monitor, required after being enabled with -a or -n
  -L, --reload                   : Signal monitor to reload settings
  -E, --enable                   : Enable detection, wake monitor up
  -D, --disable                  : Disble detection, put monitor to sleep
  -u, --suspend                  : Suspend detection, useful to prevent bogus alarms when panning etc
  -r, --resume                   : Resume detection after a suspend
  -U, --username <username>      : When running in authenticated mode the username and
  -P, --password <password>      : password combination of the given user
  -A, --auth <authentication>    : Pass authentication hash string instead of user details
ann@ann-desktop:~$ 


here i attach together the output when i run my motion software

ann@ann-desktop:~$ motion
[0] Processing thread 0 - config file /usr/local/etc/motion.conf
[0] Motion 3.2.9 Started
[0] Thread 1 is from /usr/local/etc/motion.conf
[1] Thread 1 started
[1] cap.driver: "bttv"
[1] cap.card: "BT878 video ( *** UNKNOWN/GENER"
[1] cap.bus_info: "PCI:0000:06:00.0"
[1] cap.capabilities=0x05010015
[1] - VIDEO_CAPTURE
[1] - VIDEO_OVERLAY
[1] - VBI_CAPTURE
[1] - TUNER
[1] - READWRITE
[1] - STREAMING
[1] Supported palettes:
[1] 0: GREY (8 bpp, gray)
[1] 1: HI24 (8 bpp, dithered color)
[1] 2: RGBO (15 bpp RGB, le)
[1] 3: RGBQ (15 bpp RGB, be)
[1] 4: RGBP (16 bpp RGB, le)
[1] 5: RGBR (16 bpp RGB, be)
[1] 6: BGR3 (24 bpp RGB, le)
[1] 7: BGR4 (32 bpp RGB, le)
[1] 8: RGB4 (32 bpp RGB, be)
[1] 9: YUYV (4:2:2, packed, YUYV)
[1] 10: YUYV (4:2:2, packed, YUYV)
[1] 11: UYVY (4:2:2, packed, UYVY)
[1] 12: 422P (4:2:2, planar, Y-Cb-Cr)
[1] 13: YU12 (4:2:0, planar, Y-Cb-Cr)
[1] 14: YV12 (4:2:0, planar, Y-Cr-Cb)
[1] 15: 411P (4:1:1, planar, Y-Cb-Cr)
[1] 16: YUV9 (4:1:0, planar, Y-Cb-Cr)
[1] 17: YVU9 (4:1:0, planar, Y-Cr-Cb)
[1] Test palette YU12 (352x288)
[1] Using palette YU12 (352x288) bytesperlines 352 sizeimage 152064 colorspace 00000000
[1] found control 0x00980900, "Brightness", range 0,65535 
[1]     "Brightness", default 32768, current 32768
[1] found control 0x00980901, "Contrast", range 0,65535 
[1]     "Contrast", default 32768, current 32768
[1] found control 0x00980902, "Saturation", range 0,65535 
[1]     "Saturation", default 32768, current 32768
[1] found control 0x00980903, "Hue", range 0,65535 
[1]     "Hue", default 32768, current 32768
[1] found control 0x00000000, "42", range 0,0 !DISABLED!
[1]     "42", default 0, current 32768
[1] found control 0x00000000, "42", range 0,0 !DISABLED!
[1]     "42", default 0, current 32768
[1] found control 0x00000000, "42", range 0,0 !DISABLED!
[1]     "42", default 0, current 32768
[1] found control 0x00000000, "42", range 0,0 !DISABLED!
[1]     "42", default 0, current 32768
[1] found control 0x00000000, "42", range 0,0 !DISABLED!
[1]     "42", default 0, current 32768
[1] found control 0x00000000, "42", range 0,0 !DISABLED!
[1]     "42", default 0, current 32768
[1] found control 0x08000000, "chroma agc", range 0,1 
[1]     "chroma agc", default 0, current 0
[1] found control 0x08000001, "combfilter", range 0,1 
[1]     "combfilter", default 0, current 0
[1] mmap information:
[1] frames=4
[1] 0 length=155648
[1] 1 length=155648
[1] 2 length=155648
[1] 3 length=155648
[1] Using V4L2

i cannot see image even though i have connected my analogue camera to my capture card bt878.

---

### Post by kaens on 2008-03-18
> ann@ann-desktop:~$ zmu d /dev/video0 q v

I am totally unfamiliar with the software you're using, but that should probably be:

```

zmu -d /dev/video0 -q -v

```

As a general rule, options passed at the command line are prefixed with a '-' if they are a single letter and with two '-'s ('--') if they are an entire word

---

### Post by ann pic on 2008-03-23
when i want to run xawtv got error like below:-

ann@ann-desktop:~$ xawtv 
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic) 
xinerama 0: 1024x768+0+0 
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct 
v4l2: read: Device or resource busy 
ann@ann-desktop:~$  

I found that my device is ok:-

ann@ann-desktop:~$ xawtv -hwscan 
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic) 
looking for available devices 
port 73-73 
    type : Xvideo, image scaler 
    name : Intel(R) Video Overlay 
 
/dev/video0: OK                         [ -device /dev/video0 ] 
    type : v4l2 
    name : BT878 video ( *** UNKNOWN/GENER 
    flags: overlay capture tuner  
 
hi kaens, i totally do the command like what u told me but i got problem like below:-

ann@ann-desktop:~$ zmu -d /dev/video0 -q -v 
Aborted (core dumped) 
ann@ann-desktop:~$  
 
Help me! I definitely out of idea.. anyone can help me??

---

### Post by ann pic on 2008-03-23
i am using motion software i download from [http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)

now i cannot see any output grabbed from my analogue camera.. Is it possible my camera not compatible with my driver capture card? my capture card is using BTTV driver..


This is note how to install my bttv driver..
I actually don't understand how to use the config option for the bttv.. I am afraid i haven't install the driver yet. Like what is written in the release notes for the bttv as below, for 2.6.x kernel bttv already included in the kernel just that i need to config it. I think i haven't do it yet. Help me i really run out of idea..


Release notes for bttv
======================

You'll need at least these config options for bttv:
	CONFIG_I2C=m
	CONFIG_I2C_ALGOBIT=m
	CONFIG_VIDEO_DEV=m

The latest bttv version is available from [http://bytesex.org/bttv/](http://bytesex.org/bttv/)


Make bttv work with your card
-----------------------------

Just try "modprobe bttv" and see if that works.

If it doesn't bttv likely could not autodetect your card and needs some
insmod options.  The most important insmod option for bttv is "card=n"
to select the correct card type.  If you get video but no sound you've
very likely specified the wrong (or no) card type.  A list of supported
cards is in CARDLIST.bttv

If bttv takes very long to load (happens sometimes with the cheap
cards which have no tuner), try adding this to your modules.conf:
	options i2c-algo-bit bit_test=1

For the WinTV/PVR you need one firmware file from the driver CD:
hcwamc.rbf.  The file is in the pvr45xxx.exe archive (self-extracting
zip file, unzip can unpack it).  Put it into the /etc/pvr directory or
use the firm_altera=<path> insmod option to point the driver to the
location of the file.

If your card isn't listed in CARDLIST.bttv or if you have trouble making
audio work, you should read the Sound-FAQ.


Autodetecting cards
-------------------

bttv uses the PCI Subsystem ID to autodetect the card type.  lspci lists
the Subsystem ID in the second line, looks like this:

00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 (rev 02)
        Subsystem: Hauppauge computer works Inc. WinTV/GO
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at e2000000 (32-bit, prefetchable) [size=4K]

only bt878-based cards can have a subsystem ID (which does not mean
that every card really has one).  bt848 cards can't have a Subsystem
ID and therefore can't be autodetected.  There is a list with the ID's
in bttv-cards.c (in case you are intrested or want to mail patches
with updates).


Still doesn't work?
-------------------

I do NOT have a lab with 30+ different grabber boards and a
PAL/NTSC/SECAM test signal generator at home, so I often can't
reproduce your problems.  This makes debugging very difficult for me.
If you have some knowledge and spare time, please try to fix this
yourself (patches very welcome of course...)  You know: The linux
slogan is "Do it yourself".

There is a mailing list: [email]video4linux-list@redhat.com[/email].
[https://listman.redhat.com/mailman/listinfo/video4linux-list](https://listman.redhat.com/mailman/listinfo/video4linux-list)

If you have trouble with some specific TV card, try to ask there
instead of mailing me directly.  The chance that someone with the
same card listens there is much higher...

For problems with sound:  There are alot of different systems used
for TV sound all over the world.  And there are also different chips
which decode the audio signal.  Reports about sound problems ("stereo
does'nt work") are pretty useless unless you include some details
about your hardware and the TV sound scheme used in your country (or
at least the country you are living in).


Finally: If you mail some patches for bttv around the world (to
linux-kernel/Alan/Linus/...), please Cc: me.


Have fun with bttv,

  Gerd

--
Gerd Knorr <kraxel@bytesex.org>

---

### Post by ann pic on 2008-03-24
ann@ann-desktop:~$ motion [-n] 
[0] Processing thread 0 - config file /usr/local/etc/motion.conf 
[0] Motion 3.2.9 Started 
[0] Thread 1 is from /usr/local/etc/motion.conf 
[1] Thread 1 started 
[1] cap.driver: "bttv" 
[1] cap.card: "BT878 video ( *** UNKNOWN/GENER" 
[1] cap.bus_info: "PCI:0000:06:00.0" 
[1] cap.capabilities=0x05010015 
[1] - VIDEO_CAPTURE 
[1] - VIDEO_OVERLAY 
[1] - VBI_CAPTURE 
[1] - TUNER 
[1] - READWRITE 
[1] - STREAMING 
[1] Supported palettes: 
[1] 0: GREY (8 bpp, gray) 
[1] 1: HI24 (8 bpp, dithered color) 
[1] 2: RGBO (15 bpp RGB, le) 
[1] 3: RGBQ (15 bpp RGB, be) 
[1] 4: RGBP (16 bpp RGB, le) 
[1] 5: RGBR (16 bpp RGB, be) 
[1] 6: BGR3 (24 bpp RGB, le) 
[1] 7: BGR4 (32 bpp RGB, le) 
[1] 8: RGB4 (32 bpp RGB, be) 
[1] 9: YUYV (4:2:2, packed, YUYV) 
[1] 10: YUYV (4:2:2, packed, YUYV) 
[1] 11: UYVY (4:2:2, packed, UYVY) 
[1] 12: 422P (4:2:2, planar, Y-Cb-Cr) 
[1] 13: YU12 (4:2:0, planar, Y-Cb-Cr) 
[1] 14: YV12 (4:2:0, planar, Y-Cr-Cb) 
[1] 15: 411P (4:1:1, planar, Y-Cb-Cr) 
[1] 16: YUV9 (4:1:0, planar, Y-Cb-Cr) 
[1] 17: YVU9 (4:1:0, planar, Y-Cr-Cb) 
[1] Test palette YU12 (352x288) 
[1] Using palette YU12 (352x288) bytesperlines 352 sizeimage 152064 colorspace 00000000 
[1] found control 0x00980900, "Brightness", range 0,65535  
[1]     "Brightness", default 32768, current 32768 
[1] found control 0x00980901, "Contrast", range 0,65535  
[1]     "Contrast", default 32768, current 32768 
[1] found control 0x00980902, "Saturation", range 0,65535  
[1]     "Saturation", default 32768, current 32768 
[1] found control 0x00980903, "Hue", range 0,65535  
[1]     "Hue", default 32768, current 32768 
[1] found control 0x00000000, "42", range 0,0 !DISABLED! 
[1]     "42", default 0, current 32768 
[1] found control 0x00000000, "42", range 0,0 !DISABLED! 
[1]     "42", default 0, current 32768 
[1] found control 0x00000000, "42", range 0,0 !DISABLED! 
[1]     "42", default 0, current 32768 
[1] found control 0x00000000, "42", range 0,0 !DISABLED! 
[1]     "42", default 0, current 32768 
[1] found control 0x00000000, "42", range 0,0 !DISABLED! 
[1]     "42", default 0, current 32768 
[1] found control 0x00000000, "42", range 0,0 !DISABLED! 
[1]     "42", default 0, current 32768 
[1] found control 0x08000000, "chroma agc", range 0,1  
[1]     "chroma agc", default 0, current 0 
[1] found control 0x08000001, "combfilter", range 0,1  
[1]     "combfilter", default 0, current 0 
[1] mmap information: 
[1] frames=4 
[1] 0 length=155648 
[1] 1 length=155648 
[1] 2 length=155648 
[1] 3 length=155648 
[1] VIDIOC_QBUF: Device or resource busy 
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map 
[1] V4L capturing using read is deprecated! 
[1] Motion only supports mmap. 
[1] Capture error calling vid_start 
[1] Thread finishing... 
ann@ann-desktop:~$  
 
help me.. what wrong with my video? i cannot get any output.. Anyone can help me??

---

