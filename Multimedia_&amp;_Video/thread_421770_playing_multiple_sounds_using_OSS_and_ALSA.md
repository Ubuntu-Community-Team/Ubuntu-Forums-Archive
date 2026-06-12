---
title: "playing multiple sounds using OSS and ALSA"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by kitsos on 2007-04-24
Hi,
I'm trying to set-up X-lite so that it rings while i have Totem or any other app that uses alsa open. From what i know x-lite uses OSS. When totem is open, x-lite finds that /dev/dsp is busy, otherwise it works ok. If i load it using aoss it gives a "WARNING Failed to set non=blocking mode: 6" . I tried echoing for all the pcm devices

```

echo "xtensoftphone 0 0 non-block" > /proc/asound/card0/pcm0p/oss

```

according to the alsa wiki, but nothing seems to work so far.

Also tried to modify .asoundrc :

```
ctl.!default {
  type hw
  card 0
}


pcm.dmixer  {             #this virtual device does the mixing of 
  type dmix               #the various signals
  ipc_key 1024
  slave {
    pcm "hw:0,0"
    rate 44100
  }
  bindings {
    0 0
    1 1
  }
}


pcm.!default {             
  type plug                
  slave.pcm "dmixer"
}

ctl.dsp {             
  type plug                
  slave.pcm "dmixer"
}



```

But in that case the result is the same like not using aoss (resource busy)

Can anybody help?


Thanks

---

