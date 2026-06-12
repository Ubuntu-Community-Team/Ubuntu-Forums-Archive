---
title: "SPDIF Problem"
date: 2009-07-29
forum: Mythbuntu
---

### Post by Powderking on 2009-07-29
Hi guys

I'm new to Mythbuntu and Xfce but was using Ubuntu on my Laptop for some years now. I always liked the great usability of Ubuntu and Gnome.
Now I have built a HTPC and want to use Mythbuntu on it.

Unfortunately I can't set up the sound setting. I have an Asus M4N72-E Mainboard with onboard sound and want to connect a 5.1 sound system to the SPDIF output of the board.

I have read the Ubuntu Wiki for .asound

Here's what asound -l gives me:
```
hoferr@hoferr-multimedia-m:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
```I created .asound in my home directory with the following stuff in it:
```
pcm.snd_card {
        type hw
        card 0
        device 0
}

ctl.snd_card {
        type hw
        card 0
        device 0
}

pcm.dmixer {
    type dmix
    ipc_key 1024
    ipc_perm 0666
    slave.pcm "snd_card"
    slave {
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
        channels 6
    }
    bindings {
        0 0
        1 1
        2 2
        3 3
        4 4
        5 5
    }
}

pcm.dsnooper {
    type dsnoop
    ipc_key 2048
    ipc_perm 0666 
    slave.pcm "snd_card"
    slave 
    {
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
        channels 2
    }
    bindings {
        0 0
        1 1
    }
}

pcm.duplex {
    type asym
    # Wenn man nur Stereo-Signale hat, so kann man alle upmixen lassen:
    # playback.pcm "upmix"
    # Falls nicht, so wählt man den normalen Weg
    playback.pcm "dmixer"
    # und spricht den upmix direkt an; zB "aplay -D upmix sound.wav"
    # In den allermeisten Fällen wird die Aufnahme nur Stereo sein:
    capture.pcm "dsnooper"
}

pcm.!default {
    type plug
    slave.pcm "duplex"
}

pcm.upmix {
     type route
     slave.pcm dmixer
     slave.channels 6
     ttable.0.0 1
     ttable.1.1 1
     ttable.0.2 1
     ttable.1.3 1
     ttable.0.4 0.5
     ttable.1.4 0.5
     ttable.0.5 0.5
     ttable.1.5 0.5
}
```I have tried several settings for device and also added subdevice = 1
But nothing works.

I hope there's someone who can help me...

---

### Post by nickrout on 2009-07-29
[http://www.mythtv.org/wiki/AllensDigitalAudioHowto](http://www.mythtv.org/wiki/AllensDigitalAudioHowto)

---

### Post by Powderking on 2009-07-30
Thanks alot for your answer :D

It worked for some time but now it doesn't :confused:

First of all I updated ALSA with the script from here:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Now "aplay -l" tells me:
```
hoferr@hoferr-multimedia-m:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
```With "alsamixer" I put each volume to 100% and set "IEC958", "IEC958 Default PCM" and "IEC958 1" on.

I have tested each setting for "/etc/asound.conf" from the link you have posted (except the hdmi) and the one I posted (with card = 0 and device = 1).


The speaker test "speaker-test -Dplughw:0,1" works from time to time and sometimes I can play music. 
But one doesn't work right after the other. As well it doesn't stay the same after I rebootet the system. :confused:


Maybe I have to use surround51 or iec958 from "aplay -L":
```
hoferr@hoferr-multimedia-m:~$ aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```But I have no clue... :frown:

---

### Post by Powderking on 2009-08-02
I found help in irc.freenode.net/alsa:

speaker-test -c2 -Dhw:0,1,1 was successful and with the following /etc/asound.conf I have sound over SPDIF :D
```
pcm.!default "hw:0,1,1"
```

---

### Post by Powderking on 2009-08-02
I was told this solution is better:

Under HDA-Intel.pcm.iec958.0 { ... slave.pcm { ... device 1 ... append a new line with "subdevice 1" there to /usr/share/alsa/cards/HDA-Intel.conf.

And put "pcm.!default spdif" into /etc/asound.conf

---

