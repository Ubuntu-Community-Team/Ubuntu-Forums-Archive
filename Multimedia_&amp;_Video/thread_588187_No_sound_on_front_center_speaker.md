---
title: "No sound on front center speaker"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by xpd777 on 2007-10-23
Im having trouble with my 5.1 sound. when i test the speakers with (speaker-test -Dplug:surround51 -c6-l1 -twav) I get to hear all speakers except for Front Center.

I have tried also using alsamixer, but still no avail.

I have tried the volume control alsa mixer by right clicking on the volume icon.

I cant play AC3 video files also in 5.1 mode

my setup

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

anyone got a clue on how i should configure my 5.1channel?

---

### Post by xpd777 on 2007-10-23
anyone have tried this?

[URL="http://www.cse.ohio-state.edu/%7Ebondhugu/alsamch.shtml"]
http://www.cse.ohio-state.edu/%7Ebondhugu/alsamch.shtml[/URL]

---

### Post by xpd777 on 2007-10-23
Iv tried everything already from this website 

[http://www.cse.ohio-state.edu/%7Ebondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/%7Ebondhugu/alsamch.shtml)

my asoundrc


> # for 5.1 speakers
pcm.ch51dup {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}


my rc.local

> # vi /etc/rc.local
...
echo Setting 5.1 Channel volumes... 
amixer -q set Master 100% unmute  
amixer -q set PCM 40% unmute  
amixer -q set Surround 100% unmute  
amixer -q set Center 81% unmute  
amixer -q set LFE 100% unmute  
amixer -q set "Surround Jack Mode" "Shared"  
amixer -q set "Mic select" "Mic2"   
amixer -q set "Mic" 65% unmute  
amixer -q set "Channel mode" "6ch"   
amixer -q set "Center/LFE Down mix" 100% unmute 
amixer -q set "Duplicate Front" mute   


my ICH4 copied from > [http://www.cse.ohio-state.edu/%7Ebondhugu/ICH4.conf](http://www.cse.ohio-state.edu/%7Ebondhugu/ICH4.conf)

i still cant get a sound on my front center speaker.


my alsa mixers all UNmute and 100% full volume. even from the alsamixer in the terminal

---

