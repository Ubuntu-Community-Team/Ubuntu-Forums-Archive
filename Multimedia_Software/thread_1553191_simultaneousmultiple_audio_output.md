---
title: "simultaneous/multiple audio output?"
date: 2010-08-14
forum: Multimedia Software
---

### Post by zim2dive on 2010-08-14
My primary audio output is HDMI on my NVidia GT240 card... using Alsa 1.0.23 and some edits to modprobe.conf, as detailed in the nvidia forums : [http://www.nvnews.net/vbulletin/showthread.php?t=150113](http://www.nvnews.net/vbulletin/showthread.php?t=150113)

I would like to copy/duplicate/echo the front 2 channels of audio (when listening to internet radio, etc) to the motherboard 2-ch outputs, so I can send these to Zone 2 on my AVR (most AVRs do not decode digital sources to Zone 2)

I have not been able to figure this out.. I can select HDMI or the mobo outputs, but never both at the same time.

I have tried several .asoundrc configs... none yet with success.
```
pcm.!default hdmi:NVidia
pcm:iec958 hdmi:NVidia

pcm.foo {
        type copy               # Copy PCM
        slave {                 # Slave definition
            pcm {
                    type hw;
                    card 0; 
                    device 0;
                   # subdevice 0;
            }   
        }
}
``````
pcm.!default hdmi:NVidia
pcm:iec958 hdmi:NVidia

pcm.copy {
        type hw;
        card 0; 
        device 0;
        subdevice 0;
}    

pcm.duplicate {
type copy
slave.pcm "copy"
slave.channels 2
route_policy duplicate
}
``````
pcm.!default plug:both

pcm.both {
    type copy
    slaves.a.pcm "hw:0,0"
    slaves.b.pcm "hw:0,1"
}
```
all 3 produce the same result.. I can use the Ubuntu sound panel to select HDMI *or* Analog output.. but only 1 is active at a time.

How do I do this?

other info ```
 >aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


>aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
```

padevchooser appears to have been deprecated (I've seen some suggestions it may have helped with this)

thanks,
Mike

---

### Post by stumpalump on 2011-10-16
Hey, Mike.

This thread is pretty old but I was wondering if you ever had any luck with this?  I'm trying to do basically the same thing on 11.10. I want to use TV speakers as center channel through HDMI while also using optical/coax for the surround. Any help would be appreciated!

---

### Post by zim2dive on 2011-10-16
Sorry, I never had any great luck with this and gave up.

---

### Post by stumpalump on 2011-10-16
Okay well I did find the answer and I will share it with you. Simultaneous output is possible with Pulseaudio.

Install Pulseaudio preferences

```

sudo apt-get install paprefs

```

Run paprefs and there is a checkbox to enable simultaneous output to all local sound cards.

Once you do that simply select simultaneous output as default output in sound preferences. (I prefer pavucontrol on 11.10)

---

### Post by zim2dive on 2011-10-16
> **stumpalump said:**
> Okay well I did find the answer and I will share it with you. Simultaneous output is possible with Pulseaudio.

Install Pulseaudio preferences

```

sudo apt-get install paprefs

```

Run paprefs and there is a checkbox to enable simultaneous output to all local sound cards.

Once you do that simply select simultaneous output as default output in sound preferences. (I prefer pavucontrol on 11.10)

Will file that away for possible future use.  I long ago gave up trying to use linux/ubuntu for HTPC .. using now only as a server.

---

### Post by harto on 2011-11-06
> **stumpalump said:**
> Okay well I did find the answer and I will share it with you. 
Oh my god, thank you so much for sharing this! I had been fighting with those config files for ages with no luck. Finding out that there was such a simple solution available for the whole time makes me cry and laugh at the same time... Please, stumpalump, msg me if you ever plan to visit Finland so I can buy you a beer and hug you...

---

### Post by stumpalump on 2011-12-18
Send me the plane ticket, too!

---

### Post by Ozzmosis88 on 2012-09-30
Right On!

I installed this app but it never clicked. Thanks a million!

---

