---
title: "ALSA Surround Sound - ATI IXP AC97"
date: 2010-06-11
forum: Multimedia Software
---

### Post by esoikie on 2010-06-11
Having some problems with my surround sound.  Ultimately, I'd like to listen to MP3's in Amarok using the 4 speakers and subwoofer.

some sound system information:

aplay -l output
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

aplay -L output
```

aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    Front speakers
surround40:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    4.0 Surround output to Front and Rear speakers
surround41:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=IXP,DEV=0
    ATI IXP, ATI IXP IEC958 (AC97)
    IEC958 (S/PDIF) Digital Audio Output
```

Also, here is my current .asoundrc
```
pcm.atiixp {
          type hw
          card 0
       }
       
ctl.atiixp {
          type hw
          card 0

```

Now... I have a 6 channel wav file.  When I type 'aplay 6channel.wav':
It says "Front Left" played through the front left speaker
It says "Front Right" played through the front right speaker
It says "Center" which isn't heard.  (So far so good)
***It says "Rear Left" played through the FRONT left AND right speakers.***
It says "Rear Right" played through the rear right speaker.

Also when I type ***'speaker-test' I get no sound through the rear left speaker*** under the current configuration.  At some point yesterday (I have no idea how) I did temporarily have sound in the rear left speaker, so I know it works.  However when I rebooted, I lost it.

I'd like to make sure that alsa is working and routing sound properly before I mess around with pulse.  However, I don't know if pulse settings would be affecting these 'aplay' and 'speaker-test' outputs.

---

### Post by esoikie on 2010-06-11
I've discovered that if I put 
aplay -D 'atiixp 6channel.wav', it plays them properly.

So by changing the .asoundrc to
```
pcm.!default {
          type hw
          card 0
       }
       
ctl.atiixp {
          type hw
          card 0
```

It plays properly in all 4 speakers.  However from what I understand to get 'surround' sound from my amarok, I am going to need to get some 'route_policy duplicate' line in there, but I'm not sure where or how.  I would guess that I will then hear 'front left' in both the front and rear speakers. I realize this is not 'true surround' but the best you will get from mp3's.

my alsa info is:
[http://www.alsa-project.org/db/?f=ee9e5a68332f513ed17edfc5405742cb213bd121](http://www.alsa-project.org/db/?f=ee9e5a68332f513ed17edfc5405742cb213bd121)

---

### Post by esoikie on 2010-06-11
**_RESOLVED_**
Thanks to crimson over at #alsa on freenode irc for helping me with some questions through this.  In the end, this is my commented ~/.asoundrc with custom table routing with adjusted volumes to get certain effects.  Hope my notes help somebody.

```

pcm.atiixp {
          type hw
          card 0
       }
       
ctl.atiixp {
          type hw
          card 0
}

pcm.!default {
        type plug
        slave.pcm ch41dup
        slave.channels 6
}

pcm.ch41dup {
	type route
	slave.pcm atiixp
	slave.channels 6
	ttable {
	    0.0    0.75    #FL Channel to FL Speaker .75 volume
	    1.1    0.75    #FR Channel to FR Speaker .75 volume
	    2.0    0.5     #copy center to FL at .5 volume
	    2.1    0.5     #copy center to FR at .5 volume
	    3.3    1       #enable subwoofer Set to full volume to increase bass
	    4.4    0.75    #RL Channel to RL Speaker .75 volume
	    5.5    0.75    #RR Channel to RR Speaker .75 volume
	    0.4    0.3     #copy FL to RL at .3 volume
	    1.5    0.3     #copy FR to RR at .3 volume
	 }
}

```

That got the alsa sound working how I wanted it. I tested it using the 'speaker-test' commands and 'aplay -D ch41dup 6channel.wav'.  This tested the alsa system directly without any interference from pulse audio or other audio systems. Once it was working the way I wanted then I needed to get it working with pulse & amarok..

**_Amarok w. Pulse Audio_**

to get it working in Amarok which uses pulse audio, part way down the ~/.pulse/default.pa I had to uncomment the line 
```
#load-module module-alsa-sink
```
and make it call my ch41dup pcm that was defined in my .asoundrc
```
load-module module-alsa-sink device=ch41dup
```

finally, I had to tell pulse to not automatically load drivers, which means further down the default.pa where it says
### Automatically load driver modules... comment out (Put a # before the lines) auto-module detection so it looks like this:
```

### Automatically load driver modules depending on the hardware available
#.ifexists module-udev-detect.so
# load-module module-udev-detect
# .else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
# load-module module-detect
# .endif

```

This whole process allows you to custom configure your sound routing to each of the channels using ALSA (.asoundrc) and then force pulse to utilize your customized settings.

---

### Post by esoikie on 2010-06-11
-- Modified previous post --

---

### Post by esoikie on 2010-06-11
-- Modified previous post --

---

