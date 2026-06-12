---
title: "How to &quot;claim&quot; a wireless card"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by kingaxon on 2012-05-28
Just got a new compaq presario cq57. I've been trying all day to get the wireless working. So far i've come up with pretty much no results. i've gotten ndiswrapper and the driver for my card, and it recognizes the hardware, but the wireless card is still coming up unclaimed. I've been reading every post and how-to guide i've come across, but they haven't gotten me anywhere. I know that the wireless card works, I was using it yesterday when I had windows installed.

Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01) 
10ec:8176

iwconfig only comes up with 
"lo         no wireless extensions"

sudo lshw -c network
*-network UNCLAIMED
     description: Network controller
     product: Realtek Semiconductor Co., Ltd.
     vendor: Realtek Semiconductor Co., Ltd.
     physical id: 0
     bus info: pci@0000:02:00.0
     version: 01
     width: 64 bits
     clock: 33MHz
     capabilities: pm msi pciexpress bus_master cap_list
     configuration: latency=0
     resources: ioport:3000(size=256) memory:92500000-92503fff

I'm using ubuntu 10.04.4, and the kernel is 2.6.32-41-generic i686

---

### Post by linuxman94 on 2012-05-28
Can you post the output of these commands please?

```
lspci
lsmod
uname -a
```

Use code tags (# sign in the editor).

---

### Post by kingaxon on 2012-05-28
lspci
```
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
03:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

```

lsmod
```
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203472  0 
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  17375  0 
output                  1871  1 video
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ndiswrapper           184709  0 
serio_raw               3978  0 
uvcvideo               57438  0 
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
vga16fb                11385  1 
vgastate                8961  1 vga16fb
usb_storage            40033  1 
ahci                   32680  2 

```

uname -a
```
Linux mike-laptop 2.6.32-41-generic #89-Ubuntu SMP Fri Apr 27 22:22:09 UTC 2012 i686 GNU/Linux
```

---

### Post by linuxman94 on 2012-05-28
Ok just to be sure, please post this output:

```
lspci -nn | grep Network
```

---

### Post by kingaxon on 2012-05-28
lspci -nn | grep Network
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
```

---

### Post by linuxman94 on 2012-05-28
Alright, as I suspected your card is supported by the kernel.  I need you to purge ndiswrapper with these commands.

```
sudo apt-get purge ndiswrapper* ndisgtk
```EDIT: Sorry I just double-checked the kernel version and it isn't support until kernel 2.6.38 and you have 2.6.32.

You have two options. 

1. Update to the latest LTS release (12.04)
2. Install kernel 2.6.38 in 10.04.4 with these commands:

```
sudo apt-get update
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty
```

---

### Post by chili555 on 2012-05-28
I don't believe the driver exists in 10.04. Here is a quote from one of my systems:> chili@chili-print:~$ modinfo rtl8192ce
ERROR: modinfo: could not find module rtl8192ce
chili@chili-print:~$ uname -r
2.6.32-41-genericI think his options are upgrade, compile or ... ndiswrapper.

---

### Post by kingaxon on 2012-05-28
@linuxman94
The first one worked. But when I enter the second command I get

```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module rtl8192ce not found.

```

---

### Post by linuxman94 on 2012-05-28
See my edited post, I realized the driver wasn't in the kernel you have right after I posted.

---

### Post by wildmanne39 on 2012-05-28
Hi, run ```
sudo apt-get update && sudo apt-get upgrade
``` then reboot, then run the following commands one line at a time:

```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```
that should install the driver but you will need to get rid of ndiswrapper first.

Edit: Sorry chili555 did not see you there when I started locating the directions.
Thanks

---

### Post by kingaxon on 2012-05-28
Sorry about this, but I don't have access to a wired connection, but I do have another laptop (what i've been using to post with). Is there a way to update from a flashdrive?

---

### Post by wildmanne39 on 2012-05-28
Hi, in that case I recommend downloading and making a copy of 12.04 then do a clean install.
Thanks

---

### Post by kingaxon on 2012-05-28
Thanks, to all of you for taking the time to help me. Once I get 12.04 running on my computer, I'll let you know how I make out. Again, thank you.

---

### Post by chili555 on 2012-05-28
Awesome fix, Wild Man! He'll also probably want to do:```
sudo rm /etc/modprobe.d/ndiswrapper
sudo modprobe r8192ce_pci
```We might also consolidate his *blacklist* files.

---

