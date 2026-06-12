---
title: "Sound problems after activation of 5.1 speakers"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by Mauler5858 on 2008-03-11
Ok i am currently using alsa on my system just fine.  I can play a game for instance and using exaile in the background just fine.  However i was only getting 2 channel sound.  I used the following etit to the asoundrc file  to activate my 5.1 speakers:
```

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}

```

Since then whenever i try to play media via alsa it is extremely choppy.  Also if i try to open any application that uses sound, and then try to open another app that uses sound(ie open media player, then open a game).  The first application only has access to sound.  The other app stays muted.

If i remove this configuration i go back to 2 channel sound.  I really want to get 5.1 working for media capabilities. Please help :P

---

### Post by Mauler5858 on 2008-03-11
bump

---

### Post by Mauler5858 on 2008-03-11
bump

---

