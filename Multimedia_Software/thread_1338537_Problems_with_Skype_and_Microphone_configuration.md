---
title: "Problems with Skype and Microphone configuration"
date: 2009-11-26
forum: Multimedia Software
---

### Post by iceman85 on 2009-11-26
Hi to all!

i need your help because i cannot solve by myself. I use Ubuntu 9.10 

Well....i've installed Skype from the Medibuntu package. I've done this to fix the problem about the cam green. 

My problem, now, is about PulseAudio and its configuration, or better i'm not able to follow the guide (wiki of ubuntu) to set PulseAudio and the microphone to speak on Skype with my contacts.

If i edit the file asound.conf, the final configuration to have the audio both for pc and skype, should be this:

```
pcm.!default {  
  type pulse    
}               

ctl.!default {
  type pulse
}

pcm.pulse {
  type pulse
}

ctl.pulse {
  type pulse
}

##Skype
pcm.snd_card {
        type hw
        card 0
}

pcm.dmixer {
        type dmix
        ipc_key 1024
        slave.pcm "snd_card"
        slave {
                period_size 256
                buffer_size 2048
                rate 44100
        }
}

pcm.dsnooper {
        type dsnoop
        ipc_key 2048
        slave.pcm "snd_card"

        slave {
                period_size 256
                buffer_size 2048
                rate 44100
        }
}

pcm.duplex {
        type asym
        playback.pcm "dmixer"
        capture.pcm "dsnooper"
}

pcm.!skype {
        type plug
        slave.pcm "duplex"
}

```afterwards....set the audio in Skype as "Skype" and not as "PulseAudio". But i cannot to do it, even if i edit the audio file configuration.

Someone has an idea?

Thanks in advance to all!

---

### Post by JoshStrobl on 2009-11-26
all you should need to do, when you have your webcam plugged in is go into Pulseaudio and change input to the webcam.

---

### Post by VertexPusher on 2009-11-27
Skype does not show any ALSA inputs and outputs when PulseAudio is running, because PulseAudio is supposed to do the routing. If you want Skype to use ALSA, you have to remove PulseAudio.

---

### Post by PariahVayne on 2009-11-27
```
sudo aptitude purge pulseaudio
```

---

### Post by iceman85 on 2009-11-27
Thanks!!!

i've tried to remove also PulseAudio. In that way my pc is mute. How can i use ALSA (or another application) for Skype and the audio's pc in general?

---

### Post by TDK800 on 2009-11-27
Try this, fixes mic, for skype too, and i've got pulseaudio still installed:

[http://ubuntuforums.org/showthread.php?p=8397068](http://ubuntuforums.org/showthread.php?p=8397068)

---

