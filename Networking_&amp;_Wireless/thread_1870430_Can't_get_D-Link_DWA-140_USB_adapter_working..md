---
title: "Can't get D-Link DWA-140 USB adapter working."
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by apemax on 2011-10-27
Hello all. I'm using Ubuntu 10.10. I recently got a D-Link DWA-140 USB wireless adapter but i can't get it to work. I think it's being recognised but it won't connect to my D-Link DSL-2640R router.

The output of lsusb:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3c09 D-Link System DWA-140 RangeBooster N Adapter(rev.B1) [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The output of lsmod:

```
via                    37920  2 
drm                   168092  3 via
pci_stub                1146  1 
vboxpci                15274  0 
vboxnetadp              6968  0 
vboxnetflt             16492  0 
vboxdrv               248433  3 vboxpci,vboxnetadp,vboxnetflt
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
joydev                  8767  0 
snd_hda_codec_realtek   218460  1 
snd_hda_intel          22235  0 
rt2870sta             406690  1 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
crc_ccitt               1351  1 rt2870sta
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_timer              19067  1 snd_pcm
video                  18712  0 
snd                    49102  6 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
via_agp                 5322  1 
coretemp                5326  0 
psmouse                59033  0 
output                  1883  1 video
serio_raw               4022  0 
shpchp                 29886  0 
i2c_viapro              5777  0 
agpgart                32011  2 drm,via_agp
lp                      7342  0 
parport                31492  1 lp
usbhid                 36882  0 
hid                    67742  1 usbhid
via_rhine              19038  0 
pata_via                7332  3 
sata_via                7344  0 
mii                     4425  1 via_rhine

```

As you can see the driver for it is loaded. (rt2870sta) The output of sudo lshw -C network:

```
*-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:26:5a:0a:6a:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=Ralink STA

```

The output of iwconfig:

```
wlan0     Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:-25 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The output of nm-tool:

```
NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             disconnected
  Default:           no
  HW Address:        00:26:5A:0A:6A:A4

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

```

I've put in all the right info using iwconfig that i know of but i can't connect to my router. I'm not sure where i'm going wrong so if someone could help me it would be appreciated. If you need and more info just ask. Thanks.:)

---

### Post by apemax on 2011-10-28
*Bump* Still need help.:)

---

### Post by fredcarru on 2011-12-26
From other threads updating to 10.11 should solve your problem

---

### Post by apemax on 2011-12-26
Hi. I've actually fixed this now but thanks.

---

### Post by fredcarru on 2011-12-30
I actually meant 11.10 sorry.
       If you've fixed it could you explain as I am having similar problems, I'm connected at the moment but 9 of 10  boots don't. Also could you mark the thread solved?

---

### Post by apemax on 2011-12-30
The problem i was having was i was trying to use WEP encryption but when i changed to WPA encryption it work. How far have you got with it? Is it recognized in Ubuntu? Is it just connecting with a router that your having issues with?

---

### Post by fredcarru on 2011-12-30
I'm trying WPA / WPA2
I'm using ubuntu 11.10. When first installed it appeared to work fine, but on subsequent boots it connected about 1 in 10 tries. I'm running dual boot with windows XP pro and in windows it connects every time. The network has a BTHomeHub2-67k5 with an extension. The signal strength is significantly stronger from the hub, 85% vs 25%, so I'm using that.

---

### Post by apemax on 2011-12-30
Ok could you run this command:

```
lsmod
```

and post the output from that command please?

---

### Post by fredcarru on 2011-12-30
Hi I'm using windows at the mo so will have to reboot and depending on how it's feeling reboot again so there may be a bit of a delay. I've run it before but didn't keep the result. are there any other commands e.g. iwconfig

---

### Post by fredcarru on 2011-12-30
well D-Link fired up this time here is the result fro lsmod
Module                  Size  Used by
bnep                   17923  2 
bluetooth             148839  7 bnep
binfmt_misc            17292  1 
vesafb                 13489  1 
snd_emu10k1_synth      12963  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13526  1 snd_emux_synth
ppdev                  12849  0 
arc4                   12473  2 
rt2800usb              22300  0 
rt2800lib              48717  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48114  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              272785  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211
snd_intel8x0           33318  2 
snd_emu10k1           133258  3 snd_emu10k1_synth
snd_ac97_codec        106082  2 snd_intel8x0,snd_emu10k1
ac97_bus               12642  1 snd_ac97_codec
snd_usb_audio         100880  1 
snd_usbmidi_lib        24558  1 snd_usb_audio
uvcvideo               67271  0 
snd_seq_midi           13132  0 
videodev               85626  1 uvcvideo
snd_rawmidi            25241  4 snd_seq_virmidi,snd_emu10k1,snd_usbmidi_lib,snd_seq_midi
snd_pcm                80468  4 snd_intel8x0,snd_emu10k1,snd_ac97_codec,snd_usb_audio
emu10k1_gp             12570  0 
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
gameport               15060  2 emu10k1_gp
k8temp                 12905  0 
snd_hwdep              13276  3 snd_emux_synth,snd_emu10k1,snd_usb_audio
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
parport_pc             32114  1 
snd_seq                51567  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              28932  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14172  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  23 snd_emux_synth,snd_seq_virmidi,snd_intel8x0,snd_emu10k1,snd_ac97_codec,snd_usb_audio,snd_usbmidi_lib,snd_rawmidi,snd_pcm,snd_hwdep,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  3 snd_intel8x0,snd_emu10k1,snd_pcm
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
sis190                 22575  0 
sata_sis               12703  2 
fred@fred-desktop:~$

---

### Post by apemax on 2011-12-30
Ok have a look at step 1 of this guide here:

[http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html]("http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html")

And see if black listing those drivers works. If that doesn't work un-blacklist "rt2x00usb" and see if that works.

---

### Post by fredcarru on 2011-12-31
at the moment it's firing up OK every time. Since I started this dialogue,
I've blacklisted them in case.
will try a few reboots and report.

---

### Post by fredcarru on 2011-12-31
well that well and truly stopped it. It didn't even try as though wireless networking didn't exist.
Over the last 5 reboots the only one that didn't launch was with the drivers blacklisted.
I guess I'll cal it fixed as there is no way to tell.
If it comes back I'll take an lsmon and iwconfig to see if anythings changed.
Ta for the help

---

### Post by apemax on 2012-01-01
No problem. glad to hear it's fixed.:)

---

