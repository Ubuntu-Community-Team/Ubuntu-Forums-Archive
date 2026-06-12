---
title: "Wireless issue on dv2500 hp: ubuntu 11.04"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by sd.ms on 2011-09-19
I installed ubuntu with windows 7. First time i couldnt connect to the internet using wifi so reinstalled and it just worked fine, until i restared it and then the wireless is gone. The lights in the front is orange, even if it is turned on in the right direction. Wifi is fine on windows 7 side.

How do i fix this .

plz help.

---

### Post by wildmanne39 on 2011-09-19
Hi, welcome to the forum! please open a terminal by hitting ctrl+alt+t then copy and paste these commands into it and then paste the results here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Sean_is_here on 2011-10-10
I have almost the same problem as sd.ms. The only difference is that windows 7 is completly uninstalled.
Here is what came up after I put your terminal commands in 

[U]sean@sean-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux sean-laptop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux
sean@sean-laptop:~$ sudo lshw -C network
[sudo] password for sean: 
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:55000000-55003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 68:b5:99:5a:3d:a1
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.68 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:1000(size=256) memory:52004000-52004fff(prefetchable) memory:52000000-52003fff(prefetchable)
sean@sean-laptop:~$ lspci -nn | grep -e 0280 -e 0200
01:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
sean@sean-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sean@sean-laptop:~$ rfkill list all
sean@sean-laptop:~$ lsmod
Module                  Size  Used by
usbhid                 36110  0 
hid                    67288  1 usbhid
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
snd_hda_codec_idt      52042  1 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_intel          22069  2 
vga16fb                11385  0 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
vgastate                8961  1 vga16fb
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
i915                  288963  3 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
drm_kms_helper         29329  1 i915
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                  8740  0 
drm                   163651  4 i915,drm_kms_helper
snd_timer              19098  2 snd_pcm,snd_seq
lp                      7028  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit            5028  1 i915
parport                32635  2 ppdev,lp
video                  17375  1 i915
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
uvcvideo               57406  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
output                  1871  1 video
videodev               34425  1 uvcvideo
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
psmouse                63677  0 
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
sean@sean-laptop:~$ 

If you know what the problem is that would be great. 


[/U]

---

### Post by wildmanne39 on 2011-10-10
Hi, welcome to the forum! Run these two commands in a terminal please:
```
sudo apt-get update
~$ sudo apt-get install bcmwl-kernel-source
```
Under the desktop menu System > Administration > Hardware/Additional or restricted Drivers, the STA drivers can be activated for use, then restart your computer, you will need to be hard wired to the internet for this to work. 
Thank you

---

