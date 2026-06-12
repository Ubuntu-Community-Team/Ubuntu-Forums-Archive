---
title: "My sound doesn't work in Ubuntu but it does in windows"
date: 2010-01-13
forum: Multimedia Software
---

### Post by neurostu on 2010-01-13
I've had ubuntu installed on my computer since 7.10. I'm currently running 9.10.

I did a clean install of 8.10 or 8.04 and have been doing the dist-upgrades since then.

I have never had working sound on my computer and I am finally fed up with it.  I installed windows on a seperate partition to confirm that I do infact have working hardware and my sound did work under windows.

When I run lspci I get the following output:
```


00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GTS] (rev a1)
03:00.0 SATA controller: Marvell Technology Group Ltd. 88SE6145 SATA II PCI-E controller (rev a1)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
05:02.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
 
```
It appears that my audio device is getting detected:
Code:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

When I run lsmod it appears that the kernel module is installed as well:
```


odule                  Size  Used by
binfmt_misc            16776  1 
openafs               571292  1 
vboxnetflt             92296  0 
vboxnetadp             85736  0 
vboxdrv               128552  1 vboxnetflt
snd_hda_intel         435636  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
hid_logitech           16256  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ff_memless             13320  1 hid_logitech
nvidia               9594120  26 
snd                    62628  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
psmouse                61972  0 
iptable_filter         10752  0 
ip_tables              19472  1 iptable_filter
i82975x_edac           12292  0 
ppdev                  15620  0 
sbp2                   30476  0 
joydev                 18368  0 
raw1394                32732  0 
x_tables               23044  1 ip_tables
usbhid                 42336  1 hid_logitech
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
serio_raw              13316  0 
parport_pc             40100  1 
edac_core              47404  1 i82975x_edac
agpgart                42696  1 nvidia
lp                     17156  0 
video1394              23740  0 
parport                42220  3 ppdev,parport_pc,lp
usb_storage            82880  0 
ohci1394               38576  1 video1394
ieee1394               94660  4 sbp2,raw1394,video1394,ohci1394
3c59x                  49192  0 
mii                    13312  1 3c59x
e1000e                121136  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

here is the line:
Code:

snd_hda_intel         435636  0

But when I try to configure the sound under System-->Prefs-->Sound, do devices show up under the Hardware tab, and the only device that shows up under the Output tab is: DUmmy Output.

I would really like to get sound working on my machine.... please help!
__________________

---

