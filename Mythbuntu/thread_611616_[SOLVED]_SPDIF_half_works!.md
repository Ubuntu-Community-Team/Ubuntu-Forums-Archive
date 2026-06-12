---
title: "[SOLVED] SPDIF half works!"
date: 2007-11-13
forum: Mythbuntu
---

### Post by pssturges on 2007-11-13
Hi, 
I have just today rebuilt my frontend/backend machine. It was built on fiesty and spdif worked fine for all audio.

I have used the Mythbuntu live cd for the new rebuild. SPDIF passthrough actually works, however when watching DVB channels with mpeg audio or listening to music, I get no sound.

Under feisty I used te following asound.conf: 
```

pcm.nforce-hw {
   type hw
   card 0
}
 
pcm.!default {
   type plug
   slave.pcm "nforce"
}
 
pcm.nforce {
   type dmix
   ipc_key 1234
   slave {
     pcm "hw:0,1"
     period_time 0
     period_size 1024
     buffer_size 32768
     rate 48000
   }
}
 
ctl.nforce-hw {
   type hw
   card 0
}

```

I have tried using this but it doesn't seem to change anything.

Having done a little bit of research, it seems that spdif should 'just work' in Mythbuntu. Is this true or am I missing something?

I'm using he onboard sound card on my Asus M2N mobo, which is based on the nvidia nforce 430 mcp chipset.

Thanks in advance,
Phil

---

### Post by pssturges on 2007-11-13
bump

---

### Post by pssturges on 2007-11-13
Fixed it! Seems you need to adjust the SPDIF slider in alsa up. In fiesty it had to be turned all the way down!:-k

Phil

---

