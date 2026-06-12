---
title: "sound problems with skype and SBLive 5.1"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by qrm on 2006-11-29
Ive been playing around  little and found that:

I can listen to music (both 5.1 and usual eg mp3 encoding) and sound mixing is just great, alsa is working perfectly. I have my SBLive 5.1 installed and ubuntu detected it automagically. 

problems:

not sure where to plug my microphone in, the asoundrc that allowed me to listen to non-5.1 encoded audio from all my speakers somehow switched the socets :D How can I make sure if I have microphone plugged in to correct hole? Any supersimplistic sound recording program around? I tried audacity but it only recorded the music I played on rythmbox even if I had the record setting set to microphone and i tried both choices left on my soundcard) I am sure my three speaker plugs are in right places because my 5.1 music etc are perfect).

Here is my asoundrc ```
#########################################################
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
}
########################################################
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
}

#######################################################
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want. 


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}
```

this is my aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SB Live [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 29/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SB Live [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SB Live [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

If anyone has a working setup with similar soundcard Id love to see screenshots from all of your settings in alsamixer. Some are really foreign to me, just too many things to tweak there :D

I am not sure how it affects skype but when I try to call someone I can hear the dial tone and ringing but thats just for a little time, I get an error message saying that there is a problem with sound. Not very good for a error message imho. Fortunately the windows client tells more to the one I tried calling to - she said that she got an error regarding my soundcard. 

all the help is welcome and appreciated.

Darn, I left windows because of awkward and noninformative error messages which didnt tell me what was wrong. Now with skype again ...

---

