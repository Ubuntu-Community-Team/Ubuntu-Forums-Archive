---
title: "[SOLVED] No sound in Gutsy, worked fine with Feisty"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by jonathanmotes on 2007-09-30
I had to format my drive, so I decided to go ahead and upgrade to Gutsy. After the install my sound doesn't work, I have an HP dv9428nr laptop. I used the Tribe 5 build, but I have done all updates and upgrades.

Output from aplay -l
```

aplay: device_list:204: no soundcards found...

```

Output from lspci -v:
```

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

My sound shows up as muted. Double clicking on the speaker icon in the tray shows:
```
No volume control GStreamer plugins and/or devices found.
```


Please help! 

Thanks!

---

### Post by wolfen69 on 2007-09-30
if feisty was working, why "upgrade"?  gutsy isnt much different. it will help the new user(easier install)  more than someone who already had it running good.

---

### Post by jonathanmotes on 2007-11-01
I thought I would update this thread since it is getting a lot of views. The kernel updates in the Release Candidate fixed my sound issues!

---

### Post by derfinsterling on 2008-04-26
@Wolfen69: No offense, but comments like that aren't exactly helping.

@Jonathanmotes: Just upgraded to Hardy - got the same thing as you described. I don't get how it can work in a previous version and then simply not work anymore after an *upgrade*.

---

### Post by jonathanmotes on 2008-04-26
> 
@Jonathanmotes: Just upgraded to Hardy - got the same thing as you described. I don't get how it can work in a previous version and then simply not work anymore after an *upgrade*.

Yeah, that is confusing to me also. I gave the laptop that I was using last year to my brother, so I can't verify that it doesn't work at the moment on it. He did try the Hardy Beta recently and he didn't mention any sound problems to me. Sorry I can't help!

---

