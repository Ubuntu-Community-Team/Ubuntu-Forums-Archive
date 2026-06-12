---
title: "SB X-Fi Surround 5.1 USB - ALSA Problems"
date: 2011-05-27
forum: Multimedia Software
---

### Post by Daniel350 on 2011-05-27
Hi all,

I'm having trouble after installing Lubuntu-desktop on top of a Ubuntu Server (64 bit).
I won't lie about the reason for this abomination of distributions is to achieve 64 bit Lubuntu. I used to run Ubuntu 64 straight, but didn't like Unity at all; Arch Linux was great up until now, but I'd like to settle down and focus more on productivity.

The situation is thus: I cannot manage to make my X-Fi USB sound card work without hacks, and at best it only works in some applications. I *think* it may be a bug in ALSA, but I had no problem in the latest versions of Ubuntu (11.04 as of this) and Xubuntu even (11.04?).

I can currently only play media in VLC media player using the following hack in my ~./asoundrc 
```
    pcm.!default {
        type hw
        card 1
    }
    ctl.!default {
        type hw           
        card 1
    }
```

This works as expected, but not for many applications (which fail to launch, with a error message related to below (no mixer controls))
```

    &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.24.2 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
    &#9474; Card: SB X-Fi Surround 5.1 Pro                      F1:  Help               &#9474;
    &#9474; Chip: USB Mixer                                     F2:  System information &#9474;
    &#9474; View: F3: Playback  F4: Capture  F5: All            F6:  Select sound card  &#9474;
    &#9474; Item:                                               Esc: Exit               &#9474;
    &#9474;                                                                             &#9474;
    &#9474;                                                                             &#9474;
    &#9474;                This sound device does not have any controls.                &#9474;
    &#9474;                                                                             &#9474;
    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;


```What could I be missing? Some diagnostic information (any other information on request):
```

    daniel@daniel-desktop:~$ aplay -L
    null
        Discard all samples (playback) or generate zero samples (capture)
    front:CARD=Intel,DEV=0
        HDA Intel, ALC888 Analog
        Front speakers
    surround40:CARD=Intel,DEV=0
        HDA Intel, ALC888 Analog
        4.0 Surround output to Front and Rear speakers
    surround41:CARD=Intel,DEV=0
        HDA Intel, ALC888 Analog
        4.1 Surround output to Front, Rear and Subwoofer speakers
    surround50:CARD=Intel,DEV=0
        HDA Intel, ALC888 Analog
        5.0 Surround output to Front, Center and Rear speakers
    surround51:CARD=Intel,DEV=0
        HDA Intel, ALC888 Analog
        5.1 Surround output to Front, Center, Rear and Subwoofer speakers
    surround71:CARD=Intel,DEV=0
        HDA Intel, ALC888 Analog
        7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
    iec958:CARD=Intel,DEV=0
        HDA Intel, ALC888 Digital
        IEC958 (S/PDIF) Digital Audio Output
    dmix:CARD=Intel,DEV=0
        HDA Intel, ALC888 Analog
        Direct sample mixing device
    dmix:CARD=Intel,DEV=1
        HDA Intel, ALC888 Digital
        Direct sample mixing device
    dsnoop:CARD=Intel,DEV=0
        HDA Intel, ALC888 Analog
        Direct sample snooping device
    dsnoop:CARD=Intel,DEV=1
        HDA Intel, ALC888 Digital
        Direct sample snooping device
    hw:CARD=Intel,DEV=0
        HDA Intel, ALC888 Analog
        Direct hardware device without any conversions
    hw:CARD=Intel,DEV=1
        HDA Intel, ALC888 Digital
        Direct hardware device without any conversions
    plughw:CARD=Intel,DEV=0
        HDA Intel, ALC888 Analog
        Hardware device with all software conversions
    plughw:CARD=Intel,DEV=1
        HDA Intel, ALC888 Digital
        Hardware device with all software conversions
    front:CARD=Pro,DEV=0
        SB X-Fi Surround 5.1 Pro, USB Audio
        Front speakers
    surround40:CARD=Pro,DEV=0
        SB X-Fi Surround 5.1 Pro, USB Audio
        4.0 Surround output to Front and Rear speakers
    surround41:CARD=Pro,DEV=0
        SB X-Fi Surround 5.1 Pro, USB Audio
        4.1 Surround output to Front, Rear and Subwoofer speakers
    surround50:CARD=Pro,DEV=0
        SB X-Fi Surround 5.1 Pro, USB Audio
        5.0 Surround output to Front, Center and Rear speakers
    surround51:CARD=Pro,DEV=0
        SB X-Fi Surround 5.1 Pro, USB Audio
        5.1 Surround output to Front, Center, Rear and Subwoofer speakers
    surround71:CARD=Pro,DEV=0
        SB X-Fi Surround 5.1 Pro, USB Audio
        7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
    iec958:CARD=Pro,DEV=0
        SB X-Fi Surround 5.1 Pro, USB Audio
        IEC958 (S/PDIF) Digital Audio Output
    dmix:CARD=Pro,DEV=0
        SB X-Fi Surround 5.1 Pro, USB Audio
        Direct sample mixing device
    dmix:CARD=Pro,DEV=1
        SB X-Fi Surround 5.1 Pro, USB Audio #1
        Direct sample mixing device
    dsnoop:CARD=Pro,DEV=0
        SB X-Fi Surround 5.1 Pro, USB Audio
        Direct sample snooping device
    dsnoop:CARD=Pro,DEV=1
        SB X-Fi Surround 5.1 Pro, USB Audio #1
        Direct sample snooping device
    hw:CARD=Pro,DEV=0
        SB X-Fi Surround 5.1 Pro, USB Audio
        Direct hardware device without any conversions
    hw:CARD=Pro,DEV=1
        SB X-Fi Surround 5.1 Pro, USB Audio #1
        Direct hardware device without any conversions
    plughw:CARD=Pro,DEV=0
        SB X-Fi Surround 5.1 Pro, USB Audio
        Hardware device with all software conversions
    plughw:CARD=Pro,DEV=1
        SB X-Fi Surround 5.1 Pro, USB Audio #1
        Hardware device with all software conversions
    hdmi:CARD=HDMI,DEV=0
        HDA ATI HDMI, HDMI 0
        HDMI Audio Output
    dmix:CARD=HDMI,DEV=3
        HDA ATI HDMI, HDMI 0
        Direct sample mixing device
    dsnoop:CARD=HDMI,DEV=3
        HDA ATI HDMI, HDMI 0
        Direct sample snooping device
    hw:CARD=HDMI,DEV=3
        HDA ATI HDMI, HDMI 0
        Direct hardware device without any conversions
    plughw:CARD=HDMI,DEV=3
        HDA ATI HDMI, HDMI 0
        Hardware device with all software conversions

```

P.S I also posted this question here: [http://askubuntu.com/questions/45477/sb-x-fi-surround-5-1-usb-on-lubuntu](http://askubuntu.com/questions/45477/sb-x-fi-surround-5-1-usb-on-lubuntu)
But not sure how much that is frequented in comparison to the forums.

---

### Post by zep24 on 2011-05-27
Hi,

Having fun with USB audio? Using such a peripheral without pulseaudio  usually requires some tweaking (and I guess Lubuntu doesn't include pulseaudio; if it does just disregard the rest of my post). This is not a bug in alsa.

Based on output  of  aplay -L you provided, a first step should be changing your asoundrc to this:

```
pcm.!default iec958:Pro
```

You should now have a working audio but with 2 major limitations:

- you can only play sound at a sample rate and bit depth supported by your sound card;

- USB audio peripherals don't support hardware mixing so only one application can play sound at the same time (including your system sounds.

If you want to overcome these limitations using just plain alsa you must enable software mixing using the dmix plugin.

Just try the first step and tell me if you want some help with setting up dmix.

---

### Post by Daniel350 on 2011-05-27
That gave me identical behavior to my posted ~/.asoundrc, sound still does not work in many applications.

I'm unsure a little more unsure as to what iec958 is?

Would it be worth my while installing PulseAudio? What may be the steps to get that working correctly then?

Thanks for the help :)

---

### Post by zep24 on 2011-05-28
If pulseaudio isn't installed on your system, you should try the dmix way first. Change your asoundrc to this:

```
pcm.!default {
    type plug
    slave.pcm "dmixer"
}
pcm.dsp0 {
    type plug
    slave.pcm "dmixer"
}
pcm.dmixer {
    type dmix
    ipc_key 1024
    ipc_key_add_uid true
    slave {
        pcm "hw:1,0"
	format "S16_LE"
	rate 48000
	#channels 6      
	period_time 0
        period_size 2048
	buffer_size 32768
        	}
     bindings {
        0 0
        1 1
	#2 2
	#3 3
	#4 4
	#5 5
     }
}
ctl.mixer0 {
    type hw
    card 1
}

```

That should give you a working dmix with stereo output (if you want 5.1 output just uncomment the lines I have commented out). In my case the conf above worked just fine for two peripherals ( usb speakers Bose Companion5 and FocalXS).

Depending on your sound card specifications you may have to change to the following lines in the slave section:

- rate 48000 : you may need to change 48000 to 44100 if it is the native format supported by your sound card ;

- format "S16_LE" : you may need to change "S16_LE" to the native format supported by your sound card ;

- pcm "hw:1,0" : based on your aplay -L output your Usb sound card provides two devices you may try to change "hw:1,0" to "hw:1,1" and see if it works better.

Good luck

---

