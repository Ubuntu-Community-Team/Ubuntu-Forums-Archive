---
title: "spdif over ALSA.  different setups all work, what is the difference?"
date: 2009-02-13
forum: Multimedia Software
---

### Post by allene222 on 2009-02-13
I have experimented and found several alsa.conf setups that work with spdif sound output under all conditions which are MythTV, MythMusic, Firefox.  Plus, they play with either of my two decoders.  Previously, I had solutions that would work with one decoder but not the other or with mythtv but not mythmusic so I think these are all robust.  My question is, what is the difference fundamentally, is one preferred over the others?

1) 
 pcm.!default {
     type plug
     slave {
        pcm "hw:0,1"
        format S32_LE
     }
  }

2) 
  pcm.!default {
     type plug
     slave.pcm "iec958"
  }

3) 
  pcm.!default {
     type plug
     slave.pcm "spdif"
  }

Obviously my digital card is card 0 device 1.

Like I said, these all work I just want to know what the difference is.  

I am trying to put this together for a wiki for digital sound for mythtv (yet another one).
[http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto](http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto)
(The title was suggested to me)


Allen

---

