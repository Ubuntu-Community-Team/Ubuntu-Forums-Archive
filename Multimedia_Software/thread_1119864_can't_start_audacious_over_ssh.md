---
title: "can't start audacious over ssh"
date: 2009-04-08
forum: Multimedia Software
---

### Post by starfry on 2009-04-08
Hi,

I have Audacious set up and working with Pulseaudio over the network. I have two machines, one running the Pulseaudio server daemon and another which has Audacious on it.

I can start an X session (using XDMCP) on the machine with Audacious and I can play some music and have it come out of the other machine. Great.

If I start an ssh (using ssh -X) session to the machine with Audacious, I can start it (I see the gui) but playing anything results in the below error:
```

MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

```

what is different about the ssh session that prevents this from working ?

any help much appreciated.

---

