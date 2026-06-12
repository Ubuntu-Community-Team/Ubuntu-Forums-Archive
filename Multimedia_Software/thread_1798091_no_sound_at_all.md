---
title: "no sound at all"
date: 2011-07-05
forum: Multimedia Software
---

### Post by stephenstop on 2011-07-05
I just upgraded some audio programs using a ppa and now there is no sound at all,i have been using hydrogen drum machine and ardour with jack audio and now there is no sound at all.Please help

---

### Post by lidex on 2011-07-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by stephenstop on 2011-07-06
Hey thank you for helping me.I ran that in terminal.It said it sent the info

---

### Post by lidex on 2011-07-06
The url should come up in the terminal eventually. Try again.

---

### Post by stephenstop on 2011-07-06
```


owner@owner-laptop:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2011-07-06 22:46:39--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-07-06 22:46:41--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,247      45.7K/s   in 0.6s    

2011-07-06 22:46:42 (45.7 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at 
Please inform the person helping you.





```


This is what- came and thenthe regular owner@owner-laptop and theblinking cursor

---

### Post by lidex on 2011-07-06
Try the local option and upload the txt file from your /tmp directory. Please use code tags.

---

### Post by stephenstop on 2011-07-07
Im sorry but how do i do both those.Im a newb and i have few computer skills,thanks

---

### Post by stephenstop on 2011-07-07
could you explain how to do the local option and upload it i am sorry for bieng so ignorant but i appreciate your help

---

### Post by lidex on 2011-07-07
Run the script again and when it asks if you want to upload select n. Next copy to clipboard the path it gives you. Now in terminal type in cat  followed by a space then right-click and paste in path from earlier. Press enter. Now copy and paste output into your next post.

```
cat /tmp/xxxxxxxx.txt

```

---

### Post by stephenstop on 2011-07-07
```

```clusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 15 [48%] [-12.00dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 9 [60%] [-18.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 3 [10%] [-30.00dB] [on] Capture [off]
  Front Right: Playback 3 [10%] [-30.00dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 6 [40%] [9.00dB] [on]
  Front Right: Capture 6 [40%] [9.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.ICH6 {
    control.1 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 29
        value.1 29
    }
    control.3 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Headphone Playback Switch'
        value true
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 31
        value.1 31
    }
    control.5 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Mono Playback Switch'
        value false
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Mono Playback Volume'
        value 29
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Beep Playback Switch'
        value true
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        comment.dbmin -4500
        comment.dbmax 0
        iface MIXER
        name 'Beep Playback Volume'
        value 9
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Phone Playback Switch'
        value true
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Phone Playback Volume'
        value 15
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Playback Switch'
        value true
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value 2
    }
    control.13 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Boost (+20dB)'
        value true
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Line Playback Switch'
        value true
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Line Playback Volume'
        value.0 18
        value.1 18
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'CD Playback Switch'
        value false
    }
    control.17 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'CD Playback Volume'
        value.0 25
        value.1 25
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Video Playback Switch'
        value true
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Video Playback Volume'
        value.0 3
        value.1 3
    }
    control.20 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Aux Playback Switch'
        value true
    }
    control.21 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Aux Playback Volume'
        value.0 3
        value.1 3
    }
    control.22 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PCM Playback Switch'
        value true
    }
    control.23 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'PCM Playback Volume'
        value.0 23
        value.1 23
    }
    control.24 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 2
        comment.item.0 Mic
        comment.item.1 CD
        comment.item.2 Video
        comment.item.3 Aux
        comment.item.4 Line
        comment.item.5 Mix
        comment.item.6 'Mix Mono'
        comment.item.7 Phone
        iface MIXER
        name 'Capture Source'
        value.0 Mix
        value.1 Mix
    }
    control.25 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Capture Switch'
        value true
    }
    control.26 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 15'
        comment.dbmin 0
        comment.dbmax 2250
        iface MIXER
        name 'Capture Volume'
        value.0 6
        value.1 6
    }
    control.27 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'pre 3D'
        comment.item.1 'post 3D'
        iface MIXER
        name 'PCM Out Path & Mute'
        value 'pre 3D'
    }
    control.28 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name '3D Control - Switch'
        value false
    }
    control.29 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mix
        comment.item.1 Mic
        iface MIXER
        name 'Mono Output Select'
        value Mix
    }
    control.30 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic1
        comment.item.1 Mic2
        iface MIXER
        name 'Mic Select'
        value Mic1
    }
    control.31 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        iface MIXER
        name '3D Control - Center'
        value 13
    }
    control.32 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        iface MIXER
        name '3D Control - Depth'
        value 3
    }
    control.33 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.34 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.35 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.36 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
    control.37 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 3'
        iface MIXER
        name 'IEC958 Playback AC97-SPSA'
        value 3
    }
    control.38 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'External Amplifier'
        value true
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
michael_mic
arc4
lib80211_crypt_tkip
binfmt_misc
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm_oss
snd_mixer_oss
snd_pcm
pcmcia
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
joydev
snd_seq_device
i915
dell_wmi
drm_kms_helper
snd
yenta_socket
ipw2200
ppdev
dell_laptop
drm
psmouse
rsrc_nonstatic
intel_agp
libipw
i2c_algo_bit
dcdbas
serio_raw
parport_pc
soundcore
video
pcmcia_core
lib80211
output
agpgart
snd_page_alloc
lp
parport
tg3


!!ALSA/HDA dmesg
!!------------------```

```

---

### Post by stephenstop on 2011-07-07
sorry
```









clusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 15 [48%] [-12.00dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 9 [60%] [-18.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 3 [10%] [-30.00dB] [on] Capture [off]
  Front Right: Playback 3 [10%] [-30.00dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 6 [40%] [9.00dB] [on]
  Front Right: Capture 6 [40%] [9.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.ICH6 {
    control.1 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 29
        value.1 29
    }
    control.3 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Headphone Playback Switch'
        value true
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 31
        value.1 31
    }
    control.5 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Mono Playback Switch'
        value false
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Mono Playback Volume'
        value 29
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Beep Playback Switch'
        value true
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        comment.dbmin -4500
        comment.dbmax 0
        iface MIXER
        name 'Beep Playback Volume'
        value 9
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Phone Playback Switch'
        value true
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Phone Playback Volume'
        value 15
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Playback Switch'
        value true
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value 2
    }
    control.13 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Boost (+20dB)'
        value true
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Line Playback Switch'
        value true
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Line Playback Volume'
        value.0 18
        value.1 18
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'CD Playback Switch'
        value false
    }
    control.17 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'CD Playback Volume'
        value.0 25
        value.1 25
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Video Playback Switch'
        value true
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Video Playback Volume'
        value.0 3
        value.1 3
    }
    control.20 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Aux Playback Switch'
        value true
    }
    control.21 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Aux Playback Volume'
        value.0 3
        value.1 3
    }
    control.22 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PCM Playback Switch'
        value true
    }
    control.23 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'PCM Playback Volume'
        value.0 23
        value.1 23
    }
    control.24 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 2
        comment.item.0 Mic
        comment.item.1 CD
        comment.item.2 Video
        comment.item.3 Aux
        comment.item.4 Line
        comment.item.5 Mix
        comment.item.6 'Mix Mono'
        comment.item.7 Phone
        iface MIXER
        name 'Capture Source'
        value.0 Mix
        value.1 Mix
    }
    control.25 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Capture Switch'
        value true
    }
    control.26 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 15'
        comment.dbmin 0
        comment.dbmax 2250
        iface MIXER
        name 'Capture Volume'
        value.0 6
        value.1 6
    }
    control.27 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'pre 3D'
        comment.item.1 'post 3D'
        iface MIXER
        name 'PCM Out Path & Mute'
        value 'pre 3D'
    }
    control.28 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name '3D Control - Switch'
        value false
    }
    control.29 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mix
        comment.item.1 Mic
        iface MIXER
        name 'Mono Output Select'
        value Mix
    }
    control.30 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic1
        comment.item.1 Mic2
        iface MIXER
        name 'Mic Select'
        value Mic1
    }
    control.31 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        iface MIXER
        name '3D Control - Center'
        value 13
    }
    control.32 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        iface MIXER
        name '3D Control - Depth'
        value 3
    }
    control.33 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.34 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.35 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.36 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
    control.37 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 3'
        iface MIXER
        name 'IEC958 Playback AC97-SPSA'
        value 3
    }
    control.38 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'External Amplifier'
        value true
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
michael_mic
arc4
lib80211_crypt_tkip
binfmt_misc
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm_oss
snd_mixer_oss
snd_pcm
pcmcia
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
joydev
snd_seq_device
i915
dell_wmi
drm_kms_helper
snd
yenta_socket
ipw2200
ppdev
dell_laptop
drm
psmouse
rsrc_nonstatic
intel_agp
libipw
i2c_algo_bit
dcdbas
serio_raw
parport_pc
soundcore
video
pcmcia_core
lib80211
output
agpgart
snd_page_alloc
lp
parport
tg3


!!ALSA/HDA dmesg
!!------------------















```

---

### Post by stephenstop on 2011-07-07
was that what you wanted?

---

### Post by lidex on 2011-07-07
You only got part of it. Just upload the text file as an attachment

---

### Post by stephenstop on 2011-07-07
now it wont connect,how much was missing?

---

### Post by stephenstop on 2011-07-08
it keeps doing this ```


owner@owner-laptop:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2011-07-08 00:26:06--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 



```
is there a way to tell if i have the wrong jackd or somin cuz i added a ppa to my sw repository so i could upgrade from hydrogen drum machine .9.4 to .9.5 but it ended up upgrading all kinds of stuff.it was kxstudio ppa and when i was looking in my sw repository i saw there were two that were jaunty and i have lucid{i have noidea why that was the case}So i uninstalled jackd which uninstalled ardour and other jack programs and then it was hard to reinstall them it kept telling me there were unmet dependencies.It did  upgrade alsa too{kxstudio-ppa}So i eventually got them reinstalled but still there are problems with sound when ardour and jack are bieng run.I was looking for this "ppa-purge" program hoping it would undo everything but i couldnt figure out how to install it.
so thats a wholelotof mess-ups which is probably really annoying abd i am really sorry but ive been racking my brain to fix this i really needyour help.Thank you sosososos much

---

