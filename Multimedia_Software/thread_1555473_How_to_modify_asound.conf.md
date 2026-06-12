---
title: "How to modify asound.conf  ?"
date: 2010-08-18
forum: Multimedia Software
---

### Post by alda2 on 2010-08-18
I have this sound cards in my PC:

aplay -L
> default:CARD=NVidia
HDA NVidia, ALC662 rev1 Analog
Default Audio Device
front:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
Front speakers
surround40:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Analog
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
HDA NVidia, ALC662 rev1 Digital
IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
HDA NVidia, NVIDIA HDMI
HDMI Audio Output
null
Discard all samples (playback) or generate zero samples (capture)my hardware list :aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0


What I want : Send audio signal without any modification to analog output ( device 0 ) + ( simultaneously ) downmixed to stereo to hdmi ( device 3 ).

I tried to make asound.conf :

> 
# --------------------------------------------------------------------- 
# Hardware - do not use directly 
# ---------------------------------------------------------------------
pcm.analog {
  type hw
  card 0
  device 0
}
ctl.analog {
  type hw
  card 0
}
# ---------------------------------------------------------------------
pcm.hdmi {
  type hw
  card 0
  device 3
}
ctl.hdmi {
  type hw
  card 0
}

# -------------------------------------------------------------------------
pcm.hdmi {
  type dmix
  ipc_key 1235
  slave {
    pcm "hdmi"
    period_time 0
    period_size 1024
    buffer_size 4096
    rate 48000
  }
}

ctl.hdmi {
  type hw
  card 0
}
# -------------------------------------------------------------------------
pcm.analog {
  type plug
  slave.pcm "analog"
  hint {
    show on
    description "Analog Output - Use analog outputs, converting samples, 
format, and rate as necessary."
  }
}

ctl.analog {
  type hw
  card 0
}


#-------------------------------------------------------------------------
#-------------------------------------------------------------------------

pcm.xbmc { 
type plug 
slave { 
pcm multi 
rate 48000 
channels 8
}
ttable.0.0 1.0 
ttable.1.1 1.0 
ttable.2.2 1.0 
ttable.3.3 1.0 
ttable.4.4 1.0 
ttable.5.5 1.0 
ttable.0.6 1.0 
ttable.1.7 1.0 
ttable.2.6 0.7 
ttable.3.7 0.7 
ttable.4.6 0.7 
ttable.4.7 0.7 
ttable.5.6 0.5 
ttable.5.7 0.5
}

ctl.xbmc {
  type hw
  card 0
}

pcm.multi { 
type multi 
slaves.a.pcm "analog" 
slaves.a.channels 6 
slaves.b.pcm "hdmi" 
slaves.b.channels 2 
bindings.0.slave a 
bindings.0.channel 0 
bindings.1.slave a 
bindings.1.channel 1 
bindings.2.slave a 
bindings.2.channel 2 
bindings.3.slave a 
bindings.3.channel 3 
bindings.4.slave a 
bindings.4.channel 4 
bindings.5.slave a 
bindings.5.channel 5 
bindings.6.slave b 
bindings.6.channel 0 
bindings.7.slave b 
bindings.7.channel 1
} 

ctl.multi {
  type hw
  card 0
} 


But somethink is wrong and I don't know what. Please can you help me what I'm doing wrong ? [IMG]http://forum.xbmc.org/images/smilies2/sorry8bj.gif[/IMG] and if is possible get this audio output with asound.conf modification ?

Thanks for each help

Alda

---

### Post by jmfal on 2010-08-18
Welcome to ubuntu

I`m not a sound expert, but I don`t think you can have a analog and digital(hdmi) output simutaneously with a single sound card. I may be wrong.

google: ubuntu howto: asound.conf  there`s quite a few sites that may help.

You can ask a moderator to move your thread to the multimedia/video section as most of the sound experts hang out there.

---

### Post by alda2 on 2010-08-18
Hi, thank you for your answer, but I am sure that existing asound.conf which sends stereo signal to hdmi and analog. So I hope there must be a way how to send 5.1 to analog and stereo to hdmi.

Thanks

Alda

---

### Post by Joeb454 on 2010-08-19
Thread moved to Multimedia & Video

---

### Post by jabeavers on 2010-08-19
It looks like you have pcm.analog defined twice. That might mess things up. By the way, I'm no expert on sound in linux, but I just got done configuring my asound.conf so I will do my best to help.

Also, when I would make changes to my asound.conf file, I would use speaker-test to test it, and if it didn't like something, it would report the errors in found in asound.conf. That might help.

---

