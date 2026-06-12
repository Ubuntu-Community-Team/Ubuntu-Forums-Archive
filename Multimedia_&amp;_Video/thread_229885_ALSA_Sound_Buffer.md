---
title: "ALSA Sound Buffer"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by open_coder on 2006-08-05
Whenever I play music and use my browser(firefox), the audio skips. I thought it was the audio buffer size. However, the file that everyone tells me to edit(~/.asoundrc) didn't exist. I created the file and copied all the required stuff into it, but it still skips all the time. I am really getting annoyed at this. How do I fix this problem and how do I ensure that the new file is correct?

My .asoundrc file:
```

pcm.via82xx-hw {
        type hw
        card 0
}
pcm.!default {
        type plug
        slave.pcm "via82xx"
}
pcm.via82xx {
        type dmix
        ipc_key 1234
        ipc_perm 0660
        slave {
                pcm "hw:0,0"
                period_time 0
                period_size 1024
                buffer_size 32768
                #rate 44100
                rate 48000
        }
}
ctl.via82xx-hw {
        type hw
        card 0
}

```

---

