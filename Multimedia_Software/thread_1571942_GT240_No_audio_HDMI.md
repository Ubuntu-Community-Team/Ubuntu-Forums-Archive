---
title: "GT240 No audio HDMI"
date: 2010-09-10
forum: Multimedia Software
---

### Post by agentsmith23 on 2010-09-10
I got a new video card yesterday and I have been running into some problems with getting the audio to work, It is a galaxy GT240. I have been reading about ways to fix this and apparently this card needs a newer version of Alsa, 1.0.23 to be exact. SO I updated Alsa and at this point Ubuntu seems to recognize it pretty well. I can now see the controls in alsamixer and I can see it listed in the hardware tab of sound preferences. If I try to listen to an audio file or watch a video with audio is sound preferences under the applications tab, it shows that the file is being played back I just can't hear anything.

What else can I try?

here is the output of aplay -l

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by jblock312 on 2010-09-10
Did you update the kernel too?
#7 in this thread shows how:
[http://ubuntuforums.org/showthread.php?t=1547688](http://ubuntuforums.org/showthread.php?t=1547688)
Hope it helps.
Jon

---

### Post by agentsmith23 on 2010-09-10
I haven't updated the kernel yet. I will need to try that once I get home tonight. Hopefully that works. Thanks

---

### Post by agentsmith23 on 2010-09-10
Tried updating the kernel as pointed out in the above post but still no audio. Any other ideas. Everything seems to show up fine in alsamixer and in aplay-l and in sound preferences under applications it shows that there is out put from certain applications but I don't hear anything. What else can I try?

---

### Post by Yellow Pasque on 2010-09-10
Seen this?: [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

---

### Post by agentsmith23 on 2010-09-11
Tried it and still no audio. Everything that I am seeing seems like I should have audio but I'm just not getting anything. In alsamixer I have 4 S/PDIF options. Should all of them be unmuted or just one? I currently have them all unmuted.

---

### Post by slighted on 2010-09-11
agentsmith23, give this a shot as it works for me... try replacing (create if necessary) asound.conf as well as sound.conf:

cat /etc/asound.conf 
```
pcm.!default hdmi:NVidia
pcm:iec958 hdmi:NVidia
```

cat /etc/modprobe.d/sound.conf 
```
options snd-hda-intel enable_msi=0 probe_mask=0xfff2
```

As well, you will want to delete the .asoundrc if it exists under your home dir.

```
rm ~/.asoundrc
```

Reboot and (hopefully) enjoy! ;)

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

:frown:
I do however have an issue with the level of volume under Mythbuntu 10.04... it seems too low (around 1/2 to 2/3's of what I would expect). If anyone has any input...

Ted

---

### Post by agentsmith23 on 2010-09-11
Ted, when this is working correctly how many S/PDIF options should I have in alsamixer? I am currently at work and will try your suggestion when I get home. I really hope it works.

---

### Post by slighted on 2010-09-11
agentsmith23, I only have one S/PDIF listed. That was the aplay -l from the previous post. ;)

I hope it works for you as well. :D

If not, let me know and we can compare config files to try to weed the culprit out of hiding.

Ted

---

### Post by agentsmith23 on 2010-09-12
Still no audio. I do have one S/PDIF in alsamixer and only one option in aplay -l. Which file would you like to compare? Thanks for the help it seems to be moving me in the right direction.

---

### Post by slighted on 2010-09-12
My onboard audio is disabled via BIOS. If your not planning on using the built-in audio for any reason I would suggest disabling. If not you can try modifying your sound.conf:

```
options snd-hda-intel enable_msi=0 probe_mask=0xfff2
```
to
```
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
```

If I remember correctly, I had troubles until I disabled the onboard audio...

By the way, could you post the results for:
aplay -l
aplay -L
lspci -v|grep Audio

---

### Post by agentsmith23 on 2010-09-12
I had already disabled the onboard audio and still no luck. I will send the other info when I get home from work.





> **slighted said:**
> My onboard audio is disabled via BIOS. If your not planning on using the built-in audio for any reason I would suggest disabling. If not you can try modifying your sound.conf:

```
options snd-hda-intel enable_msi=0 probe_mask=0xfff2
```
to
```
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
```

If I remember correctly, I had troubles until I disabled the onboard audio...

By the way, could you post the results for:
aplay -l
aplay -L
lspci -v|grep Audio

---

### Post by agentsmith23 on 2010-09-12
Here is the output of the three commands you asked for:

```
aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output

```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


```
lspci -v|grep Audio
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:06.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder

```

I also have a Hauppauge 1600 TV tuner installed.

---

### Post by slighted on 2010-09-12
Hmmmmm... What are you using to test audio?
Give these a shot:
```
speaker-test -c2 -D plughw:0,3
```
and
```
aplay -D plughw:0,3 /usr/share/sounds/alsa/Noise.wav
```

As well I assume from your previous posts that your running alsa-driver v1.0.23:
```
cat /proc/asound/version
```

What Nvidia driver are you running?
```
cat /proc/driver/nvidia/version
```

Let's also take a look at your HDMI codec:
```
cat /proc/asound/NVidia/codec#* | grep HDMI
```

---

### Post by agentsmith23 on 2010-09-13
Here are some more results:

I didn't hear anything:
```
aplay -D plughw:0,3 /usr/share/sounds/alsa/Noise.wav
Playing WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

```

```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Sep  8 2010 for kernel 2.6.32-24-generic (SMP).
```

```
cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
GCC version:  gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)
```

```
cat /proc/asound/NVidia/codec#* | grep HDMI
Codec: Nvidia GPU 0d HDMI/DP
  Device: name="NVIDIA HDMI", type="HDMI", device=3
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI

```

---

### Post by slighted on 2010-09-13
Maybe in your alsa-base.conf?

cat /etc/modprobe.d/alsa-base.conf 
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```

---

### Post by agentsmith23 on 2010-09-13
I compared the alsa-base.conf files and the appeared to be identical. Just to be sure I backed up mine and copied your info into mine and still no audio. I have also tried removing my Hauppauge 1600 just in case it was causing some kind of conflict and still no change. Any other ideas?

---

### Post by slighted on 2010-09-13
I'm assuming we're on the same kernel...
```
uname -a
Linux spcumc 2.6.32-24-generic #42-Ubuntu SMP x86_64 GNU/Linux
```
I forgot to mention that I assigned my user to the audio group:
```
sudo adduser username audio
```
Here is a copy of my asound.state
```
cat /etc/asound.state 
state.NVidia {
        control.1 {
                comment.access read
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Con Mask'
                value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        }
        control.2 {
                comment.access read
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Pro Mask'
                value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        }
        control.3 {
                comment.access 'read write'
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Default'
                value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        }
        control.4 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Switch'
                value true
        }
        control.5 {
                comment.access 'read write user'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 255'
                comment.tlv '0000000100000008ffffec1400000014'
                comment.dbmin -5100
                comment.dbmax 0
                iface MIXER
                name 'PCM Playback Volume'
                value.0 255
                value.1 255
        }
}
```
Let's also take a closer look at your Audio Controller:
```
sudo lspci -v|grep -A 9 Audio
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
        Subsystem: Device 196e:0699
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fcffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint, MSI 00
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```
Also have a look at your HDA-Intel.conf:
```
cat /usr/share/alsa/cards/HDA-Intel.conf 
#
# Configuration for the Intel HD audio (ICH6/ICH7)
#

<confdir:pcm/front.conf>

HDA-Intel.pcm.front.0 {
        @args [ CARD ]
        @args.CARD {
                type string
        }
        type softvol
        slave.pcm {
                type hw
                card $CARD
        }
        control {
                name "PCM Playback Volume"
                card $CARD
        }
}

# default with dmix+softvol & dsnoop
HDA-Intel.pcm.default {
        @args [ CARD ]
        @args.CARD {
                type string
        }
        type asym
        playback.pcm {
                type plug
                slave.pcm {
                        type softvol
                        slave.pcm {
                                @func concat
                                strings [ "dmix:" $CARD ]
                        }
                        control {
                                name "PCM Playback Volume"
                                card $CARD
                        }
                }
        }
        capture.pcm {
                type plug
                slave.pcm {
                        type softvol
                        slave.pcm {
                                @func concat
                                strings [ "dsnoop:" $CARD ]
                        }
                        control {
                                name "Digital Capture Volume"
                                card $CARD
                        }
                        min_dB -30.0
                        max_dB 30.0
                        resolution 121
                }
                # to avoid possible phase inversions with digital mics
                route_policy copy
        }
        hint.device 0
}

<confdir:pcm/surround40.conf>
<confdir:pcm/surround41.conf>
<confdir:pcm/surround50.conf>
<confdir:pcm/surround51.conf>
<confdir:pcm/surround71.conf>

HDA-Intel.pcm.surround40.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround51.0 cards.HDA-Intel.pcm.front.0
HDA-Intel.pcm.surround71.0 cards.HDA-Intel.pcm.front.0

<confdir:pcm/iec958.conf>

HDA-Intel.pcm.iec958.0 {
        @args [ CARD AES0 AES1 AES2 AES3 ]
        @args.CARD {
                type string
        }
        @args.AES0 {
                type integer
        }
        @args.AES1 {
                type integer
        }
        @args.AES2 {
                type integer
        }
        @args.AES3 {
                type integer
        }
        type asym
        playback.pcm {
                type hooks
                slave.pcm {
                        type hw
                        card $CARD
                        device 1
                }
                hooks.0 {
                        type ctl_elems
                        hook_args [
                        {
                                name "IEC958 Playback Default"
                                lock true
                                preserve true
                                value [ $AES0 $AES1 $AES2 $AES3 ]
                        }
                        {
                                name "IEC958 Playback Switch"
                                lock true
                                preserve true
                                value true
                        }
                        ]
                }
        }
        capture.pcm {
                type hooks
                slave.pcm {
                        type hw
                        card $CARD
                        device 1
                }
                hooks.0 {
                        type ctl_elems
                        hook_args [
                        {
                                name "IEC958 Capture Switch"
                                lock true
                                preserve true
                                value true
                        }
                        ]
                }
        }
        hint.device 1
}

<confdir:pcm/hdmi.conf>

HDA-Intel.pcm.hdmi.0 {
        @args [ CARD AES0 AES1 AES2 AES3 ]
        @args.CARD {
                type string
        }
        @args.AES0 {
                type integer
        }
        @args.AES1 {
                type integer
        }
        @args.AES2 {
                type integer
        }
        @args.AES3 {
                type integer
        }
        type hooks
        slave.pcm {
                type hw
                card $CARD
                device 3
        }
        hooks.0 {
                type ctl_elems
                hook_args [
                {
                        name "IEC958 Playback Default"
                        lock true
                        preserve true
                        value [ $AES0 $AES1 $AES2 $AES3 ]
                }
                {
                        name "IEC958 Playback Switch"
                        lock true
                        preserve true
                        value true
                }
                ]
        }
        hint.device 3
}

<confdir:pcm/modem.conf>

HDA-Intel.pcm.modem.0 {
        @args [ CARD ]
        @args.CARD {
                type string
        }
        type hw
        card $CARD
        device 6
        hint.show off
}
```
As a side-note, I have found that configuration changes can re-apply muting within the alsamixer.

---

### Post by agentsmith23 on 2010-09-13
Ok I found a few differences this time:

The asound state is missing the last part that yours has. Other than that it seems identical
```
state.NVidia {
    control.1 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.2 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.3 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
}
```


And sudo lspci -v|grep -A 9 Audio has some different info as well:


```
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: nVidia Corporation Device 072e
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fcffc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

---

### Post by slighted on 2010-09-14
Did you add your user to the audio group?

If you type **groups** on the command line you should see **audio** in the list of groups.

---

### Post by agentsmith23 on 2010-09-14
Yes I did

---

### Post by slighted on 2010-09-14
If you can, give me specifics on the model and make of your video card.
I am running the PNY GeForce GT 220 PCI (vcggt2201xpb) under the working config, I am also running the Nvidia beta drivers, but I had all working previous to the upgrade, so I don't believe it is a necessity.
I would assume the audio subsystem has something to do with your issue(s), unfortunately, I am not very well versed in the Linux audio arena.

If anyone could chime in and give a break-down, it may make things a bit easier to understand/resolve. ;)

---

### Post by agentsmith23 on 2010-09-14
Here is the videocard that I have:
[http://www.frys.com/product/6219310?site=sr:SEARCH:MAIN_RSLT_PG](http://www.frys.com/product/6219310?site=sr:SEARCH:MAIN_RSLT_PG)

---

### Post by slighted on 2010-09-16
Pulling straws here, but you may want to check your BIOS revision. I can't say without certainty that this was my solution, but I had no audio before a BIOS update (nettle2 board; 5 or 6 revs behind according to HP)... check the documentation before-hand. ;)

I assume you probably know this, but I should have been more specific and clarified that I was referring to the motherboard BIOS anyway...

---

### Post by agentsmith23 on 2010-09-16
I have already tried a few different bios versions. The newest is a beta and the one before that and no luck with either one. I'm going to try 10.10 beta later today and see if I get sound with the newer kernel that is used in 10.10.

---

### Post by videodrone on 2010-09-16
Hello Agentsmith.

I have two Nvidia 240 cards from 2 different manufacturers and got sound working on both after a few weeks of effort. This with Ubuntu 10.04 upgraded with ALSA 1.0.23. 

Note. on both my cards only device 7 seems to work. So if your onboard audio is NOT disabled then:-

speaker-test -D hw:1,7 -c2 

should give stereo white noise. Or with your on board audio DISABLED in your BIOS it would be:-

speaker-test -D hw:0,7 -c2

Devices hw:1,3 and hw:1,8 and hw:1,9 did not work for me, only hw:1,7. No error messages, just dont get sound.

Also, because my Nvidia 240 cards only seem to work on device 7, I find that I need to explicitly reference device 7 in my /etc/asound.conf file. So it reads:-

pcm.!default {
      type hw
      card 1
      device 7
}

ctl.!default {
     type hw
     card 1
}

The above is posed in many threads but I had to add the line "device 7" to make it work.

After entering this asound.conf file and re-booting, I can get sound in VLC and Mplayer by setting them to use ALSA, then  either default or hw:1,7 set as the device.

With Alsa 1.0.23 and Ubuntu 10.04 I did not need any of the modprobe settings described earlier in the thread.

Also, I upgraded the Nvidia driver to version 195 in :-

System > Administration > Hardware Drivers.

Not sure if this last bit is essential or if the nouveau driver that comes with Ubuntu "out of the box" would work.

Finally.
I tried the beta of Ubuntu 10.10 and it comes with ALSA 1.0.23 as standard so it immediately sees both the onboard audio and my HDMI audio on the Nvidia 240. But I cant get sound out of it yet. But only been trying for a day and it took me weeks to get audio to work with 10.04

If this does not help, I will post the exact sequence of events I went through from a fresh install of 10.04 to get sound in XBMC and VLC and Mplayer. 

Be nice if Pulse Audio just worked but I cant make it work hence setting everything to ALSA and explicitly setting default to hw:1,7

regards
Drone.

---

### Post by lidex on 2010-09-17
Not exactly the same hardware but a lot of info that may help here:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by agentsmith23 on 2010-09-19
I have it somewhat fixed. I am now using the latest 10.10 beta and the following is the only thing that I changed. I used some of the info from here: [http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250) post 8. Thanks lidex!

The section that I followed lead me to this command: 

```
aplay -Dplughw:0,9 /usr/share/sounds/alsa/Side_Right.wav
```

I had tried all four options that show up under aplay -l and 0,9 is the only one that played any sound.

Then I created /etc/asound.conf and inserted this code:

```
pcm.hdmi09 {
    type hw
    card 0
    device 9
}
pcm.!default hdmi09
```

Now the problem that I am having is that after each reboot I have no audio and all alsamixer options are muted except one and it isn't the one I need unmuted to get audio. The only way that I have found to get audio back is by unmuting the correct output in alsamixer and running:

```
aplay -Dplughw:0,9 /usr/share/sounds/alsa/Side_Right.wavv
```

If I just unmute the output in alsamixer I still don't have sound and this command must be run before I can hear anything.

What can I do to ensure that I have audio after rebooting? I am sure it is just a simple config file edit.

Thanks for all of the help!

---

### Post by Yellow Pasque on 2010-09-19
Put the command in /etc/rc.local

---

### Post by agentsmith23 on 2010-09-20
> **Temüjin said:**
> Put the command in /etc/rc.local


That doesn't work either.

---

### Post by agentsmith23 on 2010-09-21
Any other ideas?

---

### Post by tharsan on 2010-09-22
Try running 'sudo alsactl store' to store your alsamixer settings.

---

### Post by usererror on 2010-10-14
WOW, I really hope this helps someone. I just battled this for the last three hours.

Here is my aplay -l

```

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I upgraded also to the latest Alsa version from here: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Everything worked with no errors, but then could not get any sound still.  Until I did the sound-test fun:

```

speaker-test -Dplughw:0,7 -c2

```

I could only get sound out of the "7" device listed, as you see above, the 0 and 7 is for:

```
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
```

I did not have an /etc/asound.conf file so I created one with this:
```

pcm.!default {
type hw
card 0
device 7
}

ctl.!default {
type hw
card 0
}

```

the card 0 corresponds to the Card 0 from above and device 7 the same way.  I rebooted and I now have sound out of all the "default" sound devices. Created the asound.conf and rebooted. everything works.

---

