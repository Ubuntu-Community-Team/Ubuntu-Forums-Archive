---
title: "Blue video layer"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by kaufmannn on 2008-01-21
I am having a slight issue with my video output, it's not an end of the world "I have no video" or anything, I can watch downloaded movies and hard copy DVD's fine. One of the problem I'm having is when I use the cube effect in compiz, I remember watching flash videos on youtube of people's cubes where they pull out and spin the cube with the video playing perfectly the as it was spun. I try this and the video appears to be stuck on as a layer not touched by compiz, the video player gui (no matter the player... vlc, totem, or mplayer) moves fine. I can see through the viewing zone of the player gui, but as the geometry changes enough due to the cube movement parts of the video layer are blued out and others will be hidden behind the moving layer. 

Also, if I move the movie player screen around the video has a lag, until I stop moving I see blue (except where the video is stuck). I'm sure I could find other little instances, but the last one I've noticed regularly is if I place a window above the video, there is a blue border around the upper screen which I see in the video player, I relate this to the blurring around screen edges which I have through compiz. 

I tried to make some screenshots to help explain, yet the video shows up completely blue in the shots... not what I wanted to show as that's not what I see.

No idea if this bug has been fixed, I guess I could go post it on launchpad (I'm new to this still, don't know if that's the place I should go).

Oh, I'm running Ubuntu Gutsy 64-bit on a Toshiba A100-TA7 laptop. Integrated intel graphics at their finest.

---

### Post by BandD on 2008-03-10
I'm experiencing a similar issue.  Though in my case it only happens to my Skype video.

all other video is fine, flash, DVD, even camorama is fine.  Compiz seems to render it just fine.  But with Skype it is a different story.  More often than not I get the blue video thing if I do anything involving compiz (i.e. going to Cube View, or moving the video window around--I have it set to make the window semi-transparent when I move a window, or move another window partial over the video--the window shadow effect in compiz).  

The kicker for me is that sometimes it works flawlessly!  Though rarely.  And I'm not really sure what is different, other than something must have just loaded right that time.  Anyway, very strange.

---

### Post by gravometric on 2008-06-26
Here's a bump saying it happens to me too.  I get a blue screen (appears the color blue like the special effects "blue screen") only when I enable the cube.  If I full screen the video (whether it's video from Miro or from my Philips webcam using luvcview), most of the screen is blue except for the upper left corner of the screen which plays normally.  If I resize the video window small enough to fit in that corner and move the window to that corner, the video shows just fine.  If I use an effect like burning windows, then the particles just turn blue over the video.

I'm using Ubuntu 8.04 (Hardy Heron) with the 2.6.24.19-rt kernel on a Sony Vaio VGN-NR160E (all Intel hardware, but specifically the Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller).  I can reproduce the problem 99% of the time. The Philips SPC1000NC webcam worked beautifully all over the screen when I first plugged it in using luvcview and Skype, but I get blue ever since.

here's lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

Here's lsusb:
```
Bus 007 Device 002: ID 0471:0332 Philips 
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

...and here's lsmod:
```
Module                  Size  Used by
uvcvideo               58500  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29696  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
snd_usb_audio          84192  1 
snd_usb_lib            18432  1 snd_usb_audio
af_packet              24196  4 
snd_rtctimer            4640  1 
i915                   32512  2 
drm                    82964  3 i915
binfmt_misc            13320  1 
rfcomm                 43280  2 
l2cap                  25984  13 rfcomm
bluetooth              62564  4 rfcomm,l2cap
vboxdrv                61360  0 
sonypi                 23684  0 
ipv6                  275236  16 
ppdev                  10372  0 
acpi_cpufreq           10924  2 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_conservative     8840  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5760  0 
sbs                    15368  0 
sbshc                   7808  1 sbs
dock                   11564  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16644  1 ip_tables
sbp2                   24456  0 
parport_pc             36516  0 
lp                     13252  0 
parport                38600  3 ppdev,parport_pc,lp
loop                   19460  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8580  1 ecb
joydev                 13248  0 
pcmcia                 41260  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42400  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                78724  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10628  2 snd_usb_audio,snd_hda_intel
snd_seq_dummy           4868  0 
sony_laptop            35772  0 
snd_seq_oss            35968  0 
video                  19984  0 
iwl3945                89972  0 
output                  4736  1 video
yenta_socket           27404  1 
iwlwifi_mac80211      221284  1 iwl3945
tifm_7xx1               8576  0 
snd_seq_midi            9376  0 
rsrc_nonstatic         13696  1 yenta_socket
cfg80211               15368  1 iwlwifi_mac80211
tifm_core              11780  1 tifm_7xx1
pcmcia_core            41136  3 pcmcia,yenta_socket,rsrc_nonstatic
sky2                   47748  0 
psmouse                41104  0 
snd_rawmidi            25632  2 snd_usb_lib,snd_seq_midi
serio_raw               7940  0 
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54992  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ac                      7044  0 
snd_timer              24836  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
battery                14596  0 
snd                    57636  23 snd_usb_audio,snd_usb_lib,snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9312  1 snd
shpchp                 34708  0 
pci_hotplug            31776  1 shpchp
intel_agp              25492  1 
agpgart                34900  3 drm,intel_agp
evdev                  13312  9 
iTCO_wdt               13524  0 
pcspkr                  4224  0 
iTCO_vendor_support     4868  1 iTCO_wdt
ext3                  137480  3 
jbd                    49044  1 ext3
mbcache                 9856  1 ext3
sr_mod                 18084  0 
cdrom                  37152  1 sr_mod
sg                     36624  0 
sd_mod                 31232  5 
ata_piix               19716  0 
ohci1394               34096  0 
ieee1394               95544  2 sbp2,ohci1394
pata_acpi               8320  0 
ahci                   28676  4 
ata_generic             8452  0 
libata                160112  4 ata_piix,pata_acpi,ahci,ata_generic
scsi_mod              153196  5 sbp2,sr_mod,sg,sd_mod,libata
ehci_hcd               37644  0 
uhci_hcd               26896  0 
usbcore               146924  6 uvcvideo,snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd
thermal                16924  0 
processor              37384  4 acpi_cpufreq,thermal
fan                     5636  0 
fuse                   51604  1 

```



Totem Player works just fine.

babadeebadeebadeee That's all folks.  Thanks.
grav

---

### Post by gravometric on 2008-06-26
I had to cameraphone the screenshots because when I tried to Printscreen, it turned the whole window blue.

The pics are here:
[http://twitpic.com/2tpk](http://twitpic.com/2tpk)

and here:
[http://twitpic.com/2tpn](http://twitpic.com/2tpn)

---

### Post by BandD on 2008-06-27
I'm curious, because I've noticed another strange behavior.  Can you run the following in a terminal:

```
gstreamer-properties
```

A window will pop up.  Click the video tab and test both the output and input sections.

Then test to see if you can reproduce the blue screen.  I notice that when I do this the blue screen turns to a dark grey/black screen (which for some reason makes me feel more comfortable...) It doesn't solve the problem, but I think it points in the right direction.

I'm pretty sure that the problem is that is with different layers not compositing correctly.  I made some progress on narrowing down what the cause was a while back, but didn't have enough technical know how to figure it out.  But I can't really remember it.  I think the problem was that Compiz doesn't uses a certain image type or plugin but gstreamer or xorg or something does.  Sorry I can't be of more help.  But I definitely found some info in the compiz forums.

---

