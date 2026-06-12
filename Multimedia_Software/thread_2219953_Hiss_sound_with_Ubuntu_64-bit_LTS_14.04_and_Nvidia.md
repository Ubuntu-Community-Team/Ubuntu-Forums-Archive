---
title: "Hiss sound with Ubuntu 64-bit LTS 14.04 and Nvidia GT610"
date: 2014-04-26
forum: Multimedia Software
---

### Post by roger_moore on 2014-04-26
HI All

I've recently put together a HTPC comprising of a HP N54l microserver with a Gigabyte Nvidia GT610 graphics card for HDMI to my Toshiba TV. I am however experiencing a problem. There is a high pitched hissing noise that is emitted as soon as the login screen and desktop load. 

What I've noted is that if I adjust the tv volume or the volume under the Ubuntu sound settings by an increment it dissapears. However if I move up or down by the next set of increments then the hiss reappears. Also when I press Ctrl-Alt-F1 to use the terminal the hissing noise dissapears.

In an attempt to solve this I've removed the X.org drivers and replaced it with this driver from Nvidia "NVIDIA-Linux-x86_64-331.67" but I still have the problem. I've also tried adding in "tsched=0" to pulseaudio and that hasn't helped.

Please help I have run out of ideas :(

See below my alsa output:-

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.63
!!################################

!!Script ran on: Sat Apr 26 06:20:59 UTC 2014


!!Linux Distribution
!!------------------

Ubuntu 14.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      HP
Product Name:      ProLiant MicroServer
Product Version:      
Firmware Version:  O41    


!!Kernel Information
!!------------------

Kernel release:    3.13.0-24-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.13.0-24-generic
Library version:    1.0.27.2
Utilities version:  1.0.27.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe87c000 irq 19


!!PCI Soundcards installed in the system
!!--------------------------------------

01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

01:00.1 0403: 10de:0e08 (rev a1)
    Subsystem: 1458:3545


!!Modprobe options (Sound related)
!!--------------------------------

snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : Y


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Nvidia GPU 1c HDMI/DP
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de001c
Subsystem Id: 0x14583545
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Connection: 2
     0x08* 0x09
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="HDMI/DP,pcm=7 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Control: name="ELD", index=0, device=7
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=02, enabled=1
  Connection: 2
     0x08* 0x09
Node 0x06 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x08* 0x09
Node 0x07 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x08* 0x09
Node 0x08 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=6, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x09 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  5 Apr 26 08:13 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 Apr 26 08:13 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  3 Apr 26 08:14 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  2 Apr 26 08:14 /dev/snd/pcmC0D7p
crw-rw----+ 1 root audio 116,  1 Apr 26 08:13 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Apr 26 08:13 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Apr 26 08:13 .
drwxr-xr-x 3 root root 180 Apr 26 08:13 ..
lrwxrwxrwx 1 root root  12 Apr 26 08:13 pci-0000:01:00.1 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [NVidia]

Card hw:0 'NVidia'/'HDA NVidia at 0xfe87c000 irq 19'
  Mixer name    : 'Nvidia GPU 1c HDMI/DP'
  Components    : 'HDA:10de001c,14583545,00100100'
  Controls      : 14
  Simple ctrls  : 2
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.NVidia {
    control.1 {
        iface CARD
        name 'HDMI/DP,pcm=3 Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.2 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.4 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.5 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.6 {
        iface PCM
        device 3
        name ELD
        value ''
        comment {
            access 'read volatile'
            type BYTES
            count 0
        }
    }
    control.7 {
        iface CARD
        name 'HDMI/DP,pcm=7 Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.8 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 1
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.9 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 1
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.10 {
        iface MIXER
        name 'IEC958 Playback Default'
        index 1
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.11 {
        iface MIXER
        name 'IEC958 Playback Switch'
        index 1
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.12 {
        iface PCM
        device 7
        name ELD
        value '100008006d100000000002000000000052620b01544f53484942412d54560a20200907070000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read volatile'
            type BYTES
            count 95
        }
    }
    control.13 {
        iface PCM
        device 3
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write'
            type INTEGER
            count 8
            range '0 - 36'
        }
    }
    control.14 {
        iface PCM
        device 7
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write'
            type INTEGER
            count 8
            range '0 - 36'
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
bnep
bluetooth
nvidia
rndis_wlan
rndis_host
cdc_ether
usbnet
cfg80211
snd_hda_codec_hdmi
mii
snd_hda_intel
joydev
snd_hda_codec
snd_hwdep
snd_pcm
snd_page_alloc
snd_seq_midi
snd_seq_midi_event
kvm_amd
snd_rawmidi
snd_seq
kvm
snd_seq_device
snd_timer
k10temp
sp5100_tco
snd
drm
i2c_piix4
edac_core
edac_mce_amd
soundcore
mac_hid
parport_pc
ppdev
lp
parport
hid_generic
usbhid
hid
tg3
ptp
pps_core
ahci
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x04 0x185600f0
0x05 0x185600f0
0x06 0x585600f0
0x07 0x585600f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:


!!ALSA/HDA dmesg
!!--------------

[    9.074185] kvm: Nested Paging enabled
[    9.286239] hda_intel: Disabling MSI
[    9.286250] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    9.286294] hda-intel 0000:01:00.1: Disabling 64bit DMA
[    9.290492] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[    9.668061] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input6
[    9.668261] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input5
[    9.669056] type=1400 audit(1398492818.207:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=375 comm="apparmor_parser"
--
[   21.099603] NVRM: corruption and stability problems, and is not supported.
[   26.713955] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.


```

---

### Post by PatrickD-52761 on 2014-06-14
I'm going to be one of those "me too" people right now. I've got the same card, and am using the 331 drivers also. The TV is an Apex 32", so it's not the tv itself that's causing the issue. Right now, I'm in the process of switching to the 331 updates driver, to see if that fixes the issue. If not, then I've downloaded the 337 beta drivers from [http://www.geforce.com/drivers/results/75340](http://www.geforce.com/drivers/results/75340) (might need a # after it). I hope this fixes the issue, because I just dumped about $140.00 into the computer in order to update the graphics ($69.00 for the card and then $69.00 for a motherboard because my old one was ten years old). I don't want to have to dump more into it. Also I should note that as soon as I start seeing the "Ubuntu 14.04" splash screen, the hiss starts.

I've got to say one thing though. I've never had this many problems with an ATI card. The only problems I've had with those was my card was old enough that it wouldn't work with 12.04. I've never had good luck with nvidia cards.

Have a great day.:)
Patrick.

---

### Post by roger_moore on 2014-06-15
> **PatrickD-52761 said:**
> I'm going to be one of those "me too" people right now. I've got the same card, and am using the 331 drivers also. The TV is an Apex 32", so it's not the tv itself that's causing the issue. Right now, I'm in the process of switching to the 331 updates driver, to see if that fixes the issue. If not, then I've downloaded the 337 beta drivers from [http://www.geforce.com/drivers/results/75340](http://www.geforce.com/drivers/results/75340) (might need a # after it). I hope this fixes the issue, because I just dumped about $140.00 into the computer in order to update the graphics ($69.00 for the card and then $69.00 for a motherboard because my old one was ten years old). I don't want to have to dump more into it. Also I should note that as soon as I start seeing the "Ubuntu 14.04" splash screen, the hiss starts.

I've got to say one thing though. I've never had this many problems with an ATI card. The only problems I've had with those was my card was old enough that it wouldn't work with 12.04. I've never had good luck with nvidia cards.

Have a great day.:)
Patrick.

I've switched the cable to a better Acoustic Research HDMI cable and the problem is still there. I can't figure out what the problem is between Linux and the hardware on the graphics card. I've tried 12.04 and it does the same.

Would a ATI 6450 work better? The noise is annoying.

---

### Post by urdoggy on 2014-06-29
I'm experiencing the same issue as well. I've tried to narrow it down, and it's either an nVidia driver issue or related to ALSA, as I still get this without Pulse Audio. Different HDMI cables make no difference.

---

### Post by roger_moore on 2014-06-30
> **urdoggy said:**
> I'm experiencing the same issue as well. I've tried to narrow it down, and it's either an nVidia driver issue or related to ALSA, as I still get this without Pulse Audio. Different HDMI cables make no difference.

The only temporary solution I've found is to route the HDMI to my AV receiver. By the doing this the hiss almost disappears but if I place my ear near the tweeter of my speakers I can still hear it. I don't always use the AV receiver so the problem still needs to be figured out.

---

### Post by lidex on 2014-07-02
Its still pretty new. 
Do you have backports enabled in Software&Updates and the first four items checked
on the first tab? Then update and reboot.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

