---
title: "no connection with atheros ar8151"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by profanum on 2011-10-12
Hi,

I've just bought a new laptop and installed Ubuntu 10.04 LTS on dual boot with Window$ 7.
I have no wired nor wireless internet connection with Ubuntu.

Laptop's technical support "can't" help me and there is no drivers to download on the constructor's website.

Here are the technical specificities:
laptop: ASUS K73SV-TY025V
network: Atheros AR8151 PCI-E Gigabit Ethernet Controller (NDIS 6.20)
               802.11n Wireless LAN Card

Is there someone who can help me? I don't know very much in IT so please, be exhaustive O:)

By the way, here are the results of some bash commands ( that I've read in other discussions on this forum, but with no answer from the requested):  

**lspci**
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
03:00.0 Network controller: RaLink Device 5390
04:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)


**lspci -nn | grep 0280**
03:00.0 Network controller [0280]: RaLink Device [1814:5390]

**sudo lshw -C network**
[sudo] password for vincent: 
  *-network UNCLAIMED     
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:de200000-de20ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:dd800000-dd83ffff ioport:a000(size=128)

**iwconfig**
lo        no wireless extensions.


**lsmod**
Module                  Size  Used by
binfmt_misc             7960  1 
snd_hda_codec_realtek   279008  1 
ppdev                   6375  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
uvcvideo               62851  0 
nouveau               515227  0 
bitblit                 5811  1 fbcon
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
softcursor              1565  1 bitblit
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
ttm                    61007  1 nouveau
soundcore               8052  1 snd
drm_kms_helper         30742  1 nouveau
v4l2_compat_ioctl32    11892  1 videodev
video                  20623  0 
vga16fb                12757  1 
output                  2503  1 video
vgastate                9857  1 vga16fb
psmouse                65040  0 
serio_raw               4918  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
drm                   198886  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2 
vincent@vincent-laptop:~/Bureau$ 
vincent@vincent-laptop:~/Bureau$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
snd_hda_codec_realtek   279008  1 
ppdev                   6375  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
uvcvideo               62851  0 
nouveau               515227  0 
bitblit                 5811  1 fbcon
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
softcursor              1565  1 bitblit
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
ttm                    61007  1 nouveau
soundcore               8052  1 snd
drm_kms_helper         30742  1 nouveau
v4l2_compat_ioctl32    11892  1 videodev
video                  20623  0 
vga16fb                12757  1 
output                  2503  1 video
vgastate                9857  1 vga16fb
psmouse                65040  0 
serio_raw               4918  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
drm                   198886  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2

---

### Post by tim273 on 2012-02-17
I know this is probably way too late, but I built a computer with the same ethernet controller and I also had a problem.  What you need to do is get the AR81Family-linux-v1-1.0.1.14 driver and compile your kernel with it.  The solution is in this thread:

[http://ubuntuforums.org/showthread.php?t=1677122](http://ubuntuforums.org/showthread.php?t=1677122)

---

