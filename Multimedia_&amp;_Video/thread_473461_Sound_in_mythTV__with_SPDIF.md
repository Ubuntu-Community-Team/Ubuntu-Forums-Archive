---
title: "Sound in mythTV  with SPDIF"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by Peque on 2007-06-14
Hey Guys. 
I have changed from ArchLinux over and tryed Ubuntu MythTV guide - but having som seriuos problems about my Sound.  Normally this does the trick in Arch - BUT not in Ubuntu: 
[http://wiki.archlinux.org/index.php/Alsa#Getting_SPDIF_output]("http://wiki.archlinux.org/index.php/Alsa#Getting_SPDIF_output")

My setup is: 
Shuttle XPC 
Hauppauge PVR-500
The SPDIF output is connected directly into a amp - where all sound from the MythTV machine should go as default. But cannot even register there's a signal out.
I've have check alsamixer - that the card is unmuted 


```
root@myth:~# lspci
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

05:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
05:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

```


00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device c5d6
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        I/O ports at dc00 [size=256]
        I/O ports at d800 [size=256]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2


This machine have been working with Archlinux untill an update of the system - them everything seems to **** it all up. So I desidet to try something else so Ubuntu was the next: 

I have made the cjhanges in /var/lib/alsa/asound.state:
```
state.ICH {
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
                iface MIXER
                name 'Master Playback Volume'
                value.0 22
                value.1 22
        }
        control.3 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Center Playback Switch'
                value false
        }
        control.4 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 31'
                iface MIXER
                name 'Center Playback Volume'
                value 31
        }
        control.5 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'LFE Playback Switch'
                value false
        }
        control.6 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 31'
                iface MIXER
                name 'LFE Playback Volume'
                value 22
        }
        control.7 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Surround Playback Switch'
                value.0 false
                value.1 false
        }
        control.8 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                iface MIXER
                name 'Surround Playback Volume'
                value.0 22
                value.1 22
        }
        control.9 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Master Mono Playback Switch'
                value true
        }
        control.10 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 31'
                iface MIXER
                name 'Master Mono Playback Volume'
                value 25
        }
        control.11 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'PC Speaker Playback Switch'
                value false
        }
        control.12 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 15'
                iface MIXER
                name 'PC Speaker Playback Volume'
                value 15
        }
        control.13 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Phone Playback Switch'
                value false
        }
        control.14 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 31'
                iface MIXER
                name 'Phone Playback Volume'
                value 31
        }
        control.15 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Mic Playback Switch'
                value true
        }
        control.16 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 31'
                iface MIXER
                name 'Mic Playback Volume'
                value 17
        }
        control.17 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Mic Boost (+20dB)'
                value true
        }
        control.18 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Line Playback Switch'
                value false
        }
        control.19 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                iface MIXER
                name 'Line Playback Volume'
                value.0 20
                value.1 20
        }
        control.20 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'CD Playback Switch'
                value true
        }
        control.21 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                iface MIXER
                name 'CD Playback Volume'
                value.0 25
                value.1 25
        }
        control.22 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Aux Playback Switch'
                value false
        }
        control.23 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                iface MIXER
                name 'Aux Playback Volume'
                value.0 28
                value.1 28
        }
        control.24 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'PCM Playback Switch'
                value true
        }
        control.25 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                iface MIXER
                name 'PCM Playback Volume'
                value.0 22
                value.1 22
        }
        control.26 {
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
                value.0 Mic
                value.1 Mic
        }
        control.27 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Capture Switch'
                value true
        }
        control.28 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 15'
                iface MIXER
                name 'Capture Volume'
                value.0 0
                value.1 0
        }
        control.29 {
                comment.access 'read write'
                comment.type ENUMERATED
                comment.count 1
                comment.item.0 Mix
                comment.item.1 Mic
                iface MIXER
                name 'Mono Output Select'
                value Mic
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
                comment.access read
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Con Mask'
                value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        }
        control.32 {
                comment.access read
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Pro Mask'
                value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
        }
        control.33 {
                comment.access 'read write'
                comment.type IEC958
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Default'
                value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        }
        control.34 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'IEC958 Playback Switch'
                value true
        }
        control.35 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 1
                comment.range '0 - 3'
                iface MIXER
                name 'IEC958 Playback AC97-SPSA'
                value 3
        }
        control.36 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Duplicate Front'
                value true
        }
        control.37 {
                comment.access 'read write'
                comment.type ENUMERATED
                comment.count 1
                comment.item.0 Shared
                comment.item.1 Independent
                iface MIXER
                name 'Surround Jack Mode'
                value Shared
        }
        control.38 {
                comment.access 'read write'
                comment.type ENUMERATED
                comment.count 1
                comment.item.0 '2ch'
                comment.item.1 '4ch'
                comment.item.2 '6ch'
                iface MIXER
                name 'Channel Mode'
                value '6ch'
        }
        control.39 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'IEC958 Capture Switch'
                value false
        }
        control.40 {
                comment.access 'read write'
                comment.type ENUMERATED
                comment.count 1
                comment.item.0 PCM
                comment.item.1 'Analog In'
                comment.item.2 'IEC958 In'
                iface MIXER
                name 'IEC958 Playback Source'
                value 'IEC958 In'
        }
        control.41 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'External Amplifier'
                value true
        }
}

```

But that did not seems to do the trick. 
Each time I change control.35 (value to 0 ) and run alsactl store - it stills come back to ending up with 3??? So I really need some help doing this - Thanks and perhaps a good guiding in howto  - caurse I'm getting confused by doing this without any result at all

Per

---

### Post by newlinux on 2007-06-14
Maybe this will help:

[http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound](http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound)

What output does mythfrontend give when playing sound? Does sound from other apps work through spdif? How about sound through analog out?

Good luck.

---

