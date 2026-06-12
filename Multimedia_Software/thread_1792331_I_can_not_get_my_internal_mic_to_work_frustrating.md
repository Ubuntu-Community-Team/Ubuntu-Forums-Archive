---
title: "I can not get my internal mic to work frustrating"
date: 2011-06-28
forum: Multimedia Software
---

### Post by josephmills on 2011-06-28
Hi there and thanks for taking the time to read this.  I would like to think that I have tried everything but it is not working so I have not. Here is some info about my machine 
**lspci**
```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

**uname -a **
```
 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
```

**Gnome Alsa Mixer **

[IMG]http://img807.imageshack.us/img807/8299/screenshot19zb.png[/IMG]

[IMG]http://img402.imageshack.us/img402/2079/screenshot20y.png[/IMG]

[IMG]http://img21.imageshack.us/img21/7238/screenshot21f.png[/IMG]


**Sound Preferences**

[IMG]http://img607.imageshack.us/img607/2139/screenshot22f.png[/IMG]

[IMG]http://img217.imageshack.us/img217/7615/screenshot23j.png[/IMG]







Once again thank you so much joseph

---

### Post by josephmills on 2011-06-28
**lsmod**

```
Module                  Size  Used by
aes_i586                7280  2 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
vboxnetadp              6936  0 
vboxnetflt             18657  0 
vboxdrv               229899  2 vboxnetadp,vboxnetflt
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
xt_limit                1394  7 
xt_tcpudp               1927  7 
parport_pc             26058  0 
ipt_addrtype            1611  4 
xt_state                1014  7 
dm_crypt               11385  0 
ppdev                   5556  0 
snd_hda_codec_nvhdmi    13615  1 
snd_hda_codec_conexant    30003  1 
ip6table_filter         1275  1 
nvidia               9329739  50 
ip6_tables             11764  1 ip6table_filter
nf_nat_irc              1168  0 
nf_conntrack_irc        3348  1 nf_nat_irc
snd_hda_intel          22235  3 
nf_nat_ftp              1398  0 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
arc4                    1165  2 
nf_conntrack_ipv4      10783  9 nf_nat
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
snd_hwdep               5040  1 snd_hda_codec
nf_conntrack_ftp        5361  1 nf_nat_ftp
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
joydev                  8767  0 
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_midi            4588  0 
ath5k                 127027  0 
mac80211              233011  1 ath5k
ath                     7989  1 ath5k
iptable_filter          1302  1 
snd_rawmidi            17783  1 snd_seq_midi
agpgart                32011  1 nvidia
snd_seq_midi_event      6047  1 snd_seq_midi
ip_tables              10460  1 iptable_filter
cfg80211              142891  3 ath5k,mac80211,ath
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
shpchp                 29886  0 
soundcore                880  1 snd
hp_wmi                  5223  0 
psmouse                59033  0 
k10temp                 2607  0 
i2c_nforce2             5179  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
led_class               2633  1 ath5k
serio_raw               4022  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
video                  18712  0 
usb_storage            40204  0 
output                  1883  1 video
ahci                   19198  2 
libahci                21728  1 ahci
pata_amd                8746  0 
forcedeth              49433  0 
ramzswap                9555  0 
lzo_compress            1865  1 ramzswap

```

**/ect/modprobe.d/blacklist.conf**

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by josephmills on 2011-06-28
my alsa file  [http://www.alsa-project.org/db/?f=bcf04ee3f927f98cd3b414e9d944bf89391623b6](http://www.alsa-project.org/db/?f=bcf04ee3f927f98cd3b414e9d944bf89391623b6)

---

### Post by josephmills on 2011-06-28
> **Abdullah00 said:**
> you need to check your sound driver as well as your mic too.

Hi there thanks but I am not sure that I follow you what do you mean by "check my sound driver" sound works great I think? I know nothing about sound and mics.

---

### Post by josephmills on 2011-06-28
I hate to do this but 8UMP

---

### Post by josephmills on 2011-06-28
no one knows anything about this ? I went to a friends house and pluged in a mic and it work out of the box so I know that it is not software (I think) 


dmesg | less 
then /Mic

```
[   15.940452] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input9
[   15.940664] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input10
[   15.940819] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input11

```


lsmod | grep snd 

```
lsmod | grep snd
snd_hda_codec_nvhdmi    13615  1 
snd_hda_codec_conexant    30003  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm

```




Please any direction my brother is in the airforce in Japan and I would like to send him so vids and talk with him voip skype ect but I can not afford a mic.

---

### Post by josephmills on 2011-06-30
8ump

---

### Post by lidex on 2011-06-30
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=ideapad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by jrschrock on 2011-06-30
Same problem here. Seriously, it's that complicated of a fix? This in addition to iPod issues has me contemplating suic...er, uh, switching back.

---

### Post by josephmills on 2011-09-03
Hi again I still cant get this mic to work any ideas ?

---

### Post by lidex on 2011-09-04
> **josephmills said:**
> Hi again I still cant get this mic to work any ideas ?

Post an updated alsa-info

---

### Post by jrschrock on 2011-09-20
If he's not going to, do you mind if I do?

[http://www.alsa-project.org/db/?f=205b4b92cb1a4ebf29c5609084dc46eb86047e08](http://www.alsa-project.org/db/?f=205b4b92cb1a4ebf29c5609084dc46eb86047e08)

If that's not what you needed, I've got the report and the ALSA info script as well. Grateful for any assistance!

---

### Post by lidex on 2011-09-20
> **jrschrock said:**
> If he's not going to, do you mind if I do?

[http://www.alsa-project.org/db/?f=205b4b92cb1a4ebf29c5609084dc46eb86047e08](http://www.alsa-project.org/db/?f=205b4b92cb1a4ebf29c5609084dc46eb86047e08)

If that's not what you needed, I've got the report and the ALSA info script as well. Grateful for any assistance!
Edit your alsa-base.conf file to remove all lines beginning with [I]options snd-hda-intel
[/I]Save the changes and reboot. Now go into alsamixer and turn on the *capture 0* element using the space bar. I've not seen a setup like yours with only jack, no pulse or esd.

---

### Post by Dale61 on 2011-09-21
My audio uses pulse, but I had a similar problem with the mic not working some time ago.  What I discovered was that the internal microphone inputs as stereo, so by sliding one control to the fully off position (left), leaving the other at about 50%, then locking the sliders, the internal mic worked.  This is due to the internal mic only being a mono input.

---

### Post by josephmills on 2011-09-21
Here you go 
[http://www.alsa-project.org/db/?f=637db5bf92a54571983f7ff85a85ba87679bff0e](http://www.alsa-project.org/db/?f=637db5bf92a54571983f7ff85a85ba87679bff0e)

---

### Post by lidex on 2011-09-22
> **josephmills said:**
> Here you go 
[http://www.alsa-project.org/db/?f=637db5bf92a54571983f7ff85a85ba87679bff0e](http://www.alsa-project.org/db/?f=637db5bf92a54571983f7ff85a85ba87679bff0e)

Try changing your model selection in alsa-base.conf:
```
 
  laptop        Basic Laptop config (default)
  hp            HP Spartan laptop
  hp-dv6736     HP dv6736
  hp-f700       HP Compaq Presario F700
  ideapad       Lenovo IdeaPad laptop
  lenovo-x200   Lenovo X200 laptop
  toshiba       Toshiba Satellite M300

```
Currently ideapad is chosen.

---

### Post by thunderheights on 2012-01-03
I am having this problem as well. Any other ideas?

---

