---
title: "[SOLVED] Sound only at Login and Logout"
date: 2008-08-19
forum: Multimedia Software
---

### Post by edvar on 2008-08-19
I use my Ubuntu 8.04 as a Media Center with a high definition onboard sound card on an ASUS P5K motherboard (Realtek ALC883 with a Coaxial SPDIF) connected to my TV and my Home Theater. I was using Myth TV with Pulseaudio, all working fine. After a while I moved on to XBMC since it's more slick and the IMDB search for movie info/posters/cast is much better than MythTV. XBMC doesn't work well with Pulseaudio so I rolled my sound back to ALSA. No big deal, everything was working fine.

Last friday the sound on my computer stop working out of nowhere. I had full surround sound on it before that. Now when I start the computer there's no sound at all. When I restart X (ctrl+alt+backspace) and login again I got the KDE4.1 Login Sound for a couple of seconds and then it suddenly stops before the end of it. After that I have no sound until I logout, when I hear the logout sound fine. I tried it on GNOME and the same thing happens.

I tried everything on:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) (Comprehensive Sound Problem Solutions Guide)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

but had no success. Despite of having only one sound card on my KDE4 System Settings -> Sound I have several devices listed (in order of preference):

1. HDA Intel, ALC883 Digital (IEC (S/PDIF Digital Audio Output)
2. HDA Intel S/PDIF (Realtek ALC883)
3. HDA Intel (Realtek ALC883)
4. HDA Intel (ALC883 Analog) - Disabled
5. HDA Intel (ALC883 Digital) - Disabled
6. PulseAudio


This is my /etc/modprobe.d/alsa-base file:

[HTML]# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=6stack-dig
[/HTML]

               
Any ideas, guys?

---

### Post by edvar on 2008-08-19
Some more info...

Output of the aplay command:

[HTML]#aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/HTML]

Output of lspci:

[HTML]#lspci -vv

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 829f                             
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes                                                         
        Interrupt: pin A routed to IRQ 22                                                             
        Region 0: Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]                            
        Capabilities: [50] Power Management version 2                                                 
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)           
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-                                           
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-               
                Address: 0000000000000000  Data: 0000                                                 
        Capabilities: [70] Express Unknown type IRQ 0                                                 
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-                         
                Device: Latency L0s <64ns, L1 <1us                                                    
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-                           
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+                                  
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes                                    
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0                         
                Link: Latency L0s <64ns, L1 <1us                                                      
                Link: ASPM Disabled CommClk- ExtSynch-                                                
                Link: Speed unknown, Width x0                  [/HTML]

---

### Post by Yellow Pasque on 2008-08-19
Try this in the terminal:
```
sudo killall esd
```

If that helps, I'd recommend going into your sound preferences and disabling system sounds. My hunch is that esd isn't playing nice with all of your sound streams.

---

### Post by edvar on 2008-08-19
ESD is not running:

[HTML]$ ps aux|grep esd
ed       15519  0.0  0.0   3008   776 pts/1    S+   12:50   0:00 grep esd

$ sudo killall esd
esd: no process killed[/HTML]

I set everything to ALSA on the Multimedia Systems Selector.

---

### Post by edvar on 2008-08-20
I'll try to re-enable Pulseaudio using the steps detailed on [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) and see if it'll give me some sound playback at least for Music on Amarok and Movies on VLC. I'll worry with XBMC later...

Keep you guys posted.

---

### Post by edvar on 2008-08-20
I installed Pulseaudio but no success. Still no sound.

However I found out what's going on... I connected the Analog output of the motherboard to my receiver and changed the settings to Analog sound. Analog sound works fine however when I change back to Digital I lose all the sound! At least until I logout, when I hear the logout sound fine.

So it seems the digital sound kicks in but for some reason right after the login Ubuntu is loading the Analog driver and it's killing the Digital one, doesn't matter if it's ALSA or Pulseaudio.

Does anyone know how to fix it? Analog sound is sh*t...

---

### Post by edvar on 2008-08-20
I searched some other posts and basically to make Digital Out via SPDIF to work you need to execute alsamixer and unmute IEC958. However the IEC958 channels on my alsamixer are blank and stuck! I cannot change the volume like the other channels. The only thing I can do is mute and unmute. Also, for some reason, I have 2 separate channels: IEC958 and IEC958 DEFAULT PCM. Both unmuted but still no sound.

Tried everything here: [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut) but it's still not working.

I'm starting to get desperate. Help!!

---

### Post by MisanthropicOne on 2008-08-21
This goes to edvar:

I was having the same issue with mine, and when I installed alsamixergui, it comes up with the IEC958 with some little icon over the top of it that looks like speakers with no sound coming from them (maybe) when I just used alsamixer it said that IEC958 was turned off so I thought I'd try clicking on that little icon with alsamixergui to see if it made a difference. That icon apparently indicates whether or not the device is turned on because after clicking on it, my optical out started working.

Of course, I still have no audio with my TV with MythTV, but I'll get it worked out eventually, I think.

---

### Post by edvar on 2008-08-21
I'm not sure what happen but know it's fixed.

I installed the alsa driver version 1.17, tried some things from here [http://ubuntuforums.org/showthread.php?t=879686&highlight=spdif](http://ubuntuforums.org/showthread.php?t=879686&highlight=spdif) (I was removing the alsa packages, reinstalling and rebooting... after reading this post I remove the packages, rebooted, installed the packages and then rebooted again) and then tried your suggestion, MisanthropicOne. Now I have sound after 3 days of hassle. It shouldn't be that difficult! Anyway, that's Linux: when it's working, it's beautiful! When it's not working, it's lots of work!

About MythTv, you can check this [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut) . There's a suggestion at the end of the Howto. When I was using it I just needed to enable AC3 Passthrough on the Myth Configuration. If you wanna try more things, go here [http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF](http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF)

---

### Post by edvar on 2008-09-01
Actually this is not solved. I keep loosing all sound at least once a week.
Every time it happens I have to:

$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
$ sudo init 6
$ sudo apt-get install alsa-base alsa-utils fast-user-switch-applet gdm gdm-themes kubuntu-kde4-desktop linux-sound-base
$ sudo init 6

After that I have my digital sound back.

This is really annoying...

---

