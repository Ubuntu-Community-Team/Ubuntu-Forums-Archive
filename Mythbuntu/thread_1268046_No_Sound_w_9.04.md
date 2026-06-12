---
title: "No Sound w/ 9.04"
date: 2009-09-16
forum: Mythbuntu
---

### Post by Whiplash78 on 2009-09-16
I installed 9.04 (64 bit) last night with the nvidia graphics, and I have no sound at all, neither in mythtv, or in the OS itself.  I checked the mixer (aumixer, alsamixer, et al) to make sure nothing was muted that shouldn't be.

When I reinstall without the nvidia graphics, I have sound.  So obviously, this is some kind of problem with the nvidia drivers that I can't get my head around.  I'm at work now, so I can't post any kind of diagnostics or specs.  The mainboard is an MSI with an HDMI interface built in.

If anyone has any quick tips or websites I could try, it will be greatly appreciated.

---

### Post by rnelson0 on 2009-09-18
I have had this same problem with 8.10 and above. I'm stuck running 8.04 right now because I otherwise have no sound. I wish I had a solution for it.

---

### Post by klc5555 on 2009-09-18
> **Whiplash78 said:**
> I installed 9.04 (64 bit) last night with the nvidia graphics, and I have no sound at all, neither in mythtv, or in the OS itself.  I checked the mixer (aumixer, alsamixer, et al) to make sure nothing was muted that shouldn't be.

When I reinstall without the nvidia graphics, I have sound.  So obviously, this is some kind of problem with the nvidia drivers that I can't get my head around.  I'm at work now, so I can't post any kind of diagnostics or specs.  The mainboard is an MSI with an HDMI interface built in.

If anyone has any quick tips or websites I could try, it will be greatly appreciated.

Take a look (using lsmod) at the various sound/sound card modules that load when you're running non-NVidia graphics. Check also the output of lspci, as to how the sound controller is listed. Check again (with lsmod and lspci) when the NVidia graphics are loaded. If the sound modules are not loaded now, and the sound device no longer turns up properly with lspci, then that's where your conflict is. The problem may be virtual memory allocation with the nvidia driver at boot.

---

### Post by getafix35 on 2009-09-21
I am having a similar problem but my audio is via onboard SPDIF. I have tried the above suggestions but to no avail.
I am a very newbie at this so am busy trawling to web to try and solve the hassle

---

### Post by bsntech on 2009-09-21
getafix,

I have a tutorial on my website on how I setup MythTV on my system.  I also use SPDIF on my system.

You may try the steps I have outlined on my site - which is the very first part of the tutorial I created.  I had to install a PulseAudio program and set some config seettings in a file.  I have sound with Firefox, startup/shutdown sounds, and MythTV.

also - in MythTV when it asks for the sound card to use, ensure you choose the ALSA:SPDIF for your audio output device and IEC958 for your passthrough audio device.

[http://www.bsntech.com/content/view/591/281/]("http://www.bsntech.com/content/view/591/281/")

---

### Post by Whiplash78 on 2009-09-22
Well after days and days......and days, of hitting my head against the wall, I've decided to just go back to 8.04... something that actually works.  I've got the volume meter in pulseaudio working like the stream is there, but it's not getting to the speakers, and I've wasted too much time trying to figure out why.  For posterity's sake, here's some hardware details.

Gigabyte GA-73PVM-S2H.

lsmod
```
Module                  Size  Used by
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
nfsd                  227756  13 
auth_rpcgss            42144  1 nfsd
exportfs               12544  1 nfsd
nfs                   266344  0 
lockd                  74156  2 nfsd,nfs
nfs_acl                11136  2 nfsd,nfs
sunrpc                195424  15 nfsd,auth_rpcgss,nfs,lockd,nfs_acl
jfs                   187620  1 
lp                     17156  0 
arc4                    9856  2 
lgdt330x               16388  1 
ecb                    10752  2 
cx88_dvb               29444  0 
cx88_vp3054_i2c        10624  1 cx88_dvb
tuner_simple           22544  2 
tuner_types            22400  1 tuner_simple
tda9887                18564  2 
tda8290                20740  0 
snd_hda_intel         435636  4 
tuner                  32836  0 
snd_seq_dummy          10756  0 
cx88_alsa              18824  1 
snd_seq_oss            37760  0 
rt61pci                29572  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_seq_midi           14336  0 
crc_itu_t              10112  1 rt61pci
snd_pcm                82948  4 snd_hda_intel,cx88_alsa,snd_pcm_oss
snd_rawmidi            29696  1 snd_seq_midi
rt2x00pci              15616  1 rt61pci
rt2x00lib              37888  2 rt61pci,rt2x00pci
cx8802                 24068  1 cx88_dvb
cx8800                 38148  0 
cx88xx                 79272  4 cx88_dvb,cx88_alsa,cx8802,cx8800
led_class              12036  1 rt2x00lib
ir_common              52228  1 cx88xx
mac80211              217208  2 rt2x00pci,rt2x00lib
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
i2c_algo_bit           14084  2 cx88_vp3054_i2c,cx88xx
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
videobuf_dvb           15236  3 cx88_dvb,cx8802,cx88xx
dvb_core               92032  3 lgdt330x,cx88_dvb,videobuf_dvb
videodev               41600  3 tuner,cx8800,cx88xx
v4l1_compat            21764  1 videodev
compat_ioctl32          9344  1 cx8800
v4l2_common            20992  2 tuner,cx8800
tveeprom               20100  1 cx88xx
cfg80211               38032  2 rt2x00lib,mac80211
nvidia               7233756  28 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lirc_streamzap         20996  0 
videobuf_dma_sg        20484  5 cx88_dvb,cx88_alsa,cx8802,cx8800,cx88xx
videobuf_core          26500  5 cx8802,cx8800,cx88xx,videobuf_dvb,videobuf_dma_sg
btcx_risc              13064  4 cx88_alsa,cx8802,cx8800,cx88xx
ppdev                  15620  0 
pcspkr                 10496  0 
eeprom_93cx6           10240  1 rt61pci
agpgart                42696  1 nvidia
snd                    62628  19 snd_hda_intel,cx88_alsa,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
lirc_dev               19892  1 lirc_streamzap
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
psmouse                61972  0 
serio_raw              13316  0 
usbhid                 42336  0 
usb_storage            82880  0 
forcedeth              61712  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

lspci
```
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7100/nForce 630i (rev a2)
01:05.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:05.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:05.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:05.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
01:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

---

