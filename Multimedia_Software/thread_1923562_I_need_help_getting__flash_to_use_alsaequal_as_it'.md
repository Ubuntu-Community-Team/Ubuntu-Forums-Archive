---
title: "I need help getting  flash to use alsaequal as it's default sound device"
date: 2012-02-10
forum: Multimedia Software
---

### Post by l0vot on 2012-02-10
I am using alsaequal without pulseaudio, totem automagically routed itself through the EQ with the /etc/asound.conf i have, audacity had to be told to use plugequal as it's playback device to work, and flash absolutly refused to go through the EQ, in fact flash must be the only input to work at all. If another program is using alsaequal before flash, alsa must be restarted to get any sound at all, and if flash has sound then no other programs have sound, and alsa must be restarted in order for them to work. When flash has sound it remains completely un-equalized. Is there any way to specify the sound device flash outputs to?

Here is my complete /etc/asound.conf file, please tell me what I am doing wrong, and how to fix it.

pcm.dmixer {
    type dmix
    ipc_key 1024 
   slave {
        pcm {
        type hw
        card 0 #SB
        device 0
    } 
    buffer_size 1024 
    }
}

ctl.equal {
  type equal;
}

pcm.plugequal {
  type equal
  slave.pcm "plug:dmixer" 
  #needs "plug:" cause of floating point transition
}

ctl.!default {
    type hw
    card SB
}

pcm.!default {
  type plug
  slave {pcm "plugequal"}
}

---

