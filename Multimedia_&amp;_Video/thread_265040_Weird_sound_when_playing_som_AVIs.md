---
title: "Weird sound when playing som AVIs"
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by jackuess on 2006-09-25
I've just got Linux up and running with my new ASRock Dual939-VSTA mobo. I enjoy watching movies and tv-series on my computer so I installed Automatix to get the right codecs. However sound the sound output is realy weird when I play most of my AVIs. Some work just fine, and all the MP3s I've tested works with no complications. The sound is sort of off pitch, cann't realy describe it properly, it just sounds realy weird.
I've searched both this forum and the Internet, using google but I can't find anyone with the same issues with the onbord audio of the ASRock mobo. It seams to be a fairly popular motherboard and many peple have had other issues (with onboard NIC for example), so i think it's rather odd that I can't find a solution here or elsewhere. Would appretiate if you guys could give me a push in the right direction.

---

### Post by croak77 on 2006-09-25
What are you using to play your avi's? Have you tried different players, mplayer, xine, or vlc?

---

### Post by jackuess on 2006-09-25
I've tried VLC, MPlay and totem.

---

### Post by jackuess on 2006-09-25
It seams like the AVIs that are working are typically very small ones. I tested the music videos that I have encoded for my DAP and they all worked. They are all around 10 MB.

---

### Post by jackuess on 2006-09-26
OK I've figured it out. It seems like audio with a sample rate other than 44100 Hz sounds distorted. I found a hint about it on the Internet, so I converted one of my MP3s to be in sample rate 48000 Hz, and the sound was indeed distorted. My AVIs that doesn't work are all encoded in 48000 Hz.

So now I know when the problem appears, but it's still not fixed. There must be a workaround. How can I tell ALSA to resample all audio to 41000 Hz?

---

### Post by jackuess on 2006-09-27
I've made some progress! After some research on ALSA configuration I wrote this .asoundrc file:
```

pcm.!default {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:0,0" #for ICE1724's analog output
        #pcm "hw:0,1" # for ICE1724's digital output
        #format S32_LE # needed only for ICE1724's digital output.
        period_size 1024
        buffer_size 4096
        rate 44100
    }
}

```
It's suppose to change the sampling rate to 44100 Hz. This works in mplayer (not the gtk version, gmplayer though) but not in any other player I've tested (VLC och totem). Why is this?

---

### Post by flipkick on 2006-10-04
excellent. this indeed works perfecly for me in gmplayer. Thanks !

---

