---
title: "asoundrc, use both speakers and hdmi?"
date: 2009-06-04
forum: Multimedia Software
---

### Post by sherl0k on 2009-06-04
could a kind soul explain how to use an .asoundrc so audio comes out of both my HDMI and the speakers? 0,0 is analog speakers, 0,3 is the HDMI output. I know there's something with dmix involved but all the configuration is really cryptic.

---

### Post by sherl0k on 2009-06-05
Well, I got part of it down.

```
pcm.!default {
        type multi;
        slaves.a.pcm "hw:0,0";
        slaves.a.channels 2;
        slaves.b.pcm "hw:0,3";
        slaves.b.channels 2;
        bindings.0.slave a;
        bindings.0.channel 0;
        bindings.1.slave a;
        bindings.1.channel 1;
        bindings.2.slave b;
        bindings.2.channel 0;
        bindings.3.slave b;
        bindings.3.channel 1;
}
 
ctl.!default {
        type hw;
        card 0;
}
```

Running the test in sound preferences, audio comes out of both my TV and my speakers. But when I use any app like audacious or firefox, I get no sound at all.

---

