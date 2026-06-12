---
title: "Unusable display after resume from suspend to ram - HP NC6230 / Karmic"
date: 2010-04-20
forum: Multimedia Software
---

### Post by Craigwell on 2010-04-20
I've been nagged by this issue for a couple months now, since picking up an NC6230. 

This uses the ATI x300 minipci video card. 

The system already had an oem install of xp on it, after which I installed 9.10 on dual boot, and everything works great except:

I can suspend to ram, and resume just fine, but my main / lvds display starts blank, and then slowly morphs into this: 

[http://imagebin.org/93723](http://imagebin.org/93723)

It's rather psychedelic, but completely useless. 

I have tried fglrx (which If I understand correctly doesn't properly support my x300 anyhow) and have gone back to open source drivers. 

The interesting part of this, is that the system is still responsive, i.e. I can hit ctrl-alt-f1 and then get the system to soft reboot - even showing me the ubuntu logo once it does... 

Also interesting is that my secondary display will work fine through all of this. I can use the secondary display on resume, while the primary sits there looking like that imagebin post. 

I have tried restarting x, as well as turning the display off and on, changing resolution with xrandr, etc when this happens, no luck. 

I am hoping to either figure out a solution or a workaround - can the display be otherwise reinitialized for example?? The maddening thing is seeing the ubuntu logo pop up just fine when i go for the soft reboot. Surely there's something I can do. 

This does not happen, btw if I suspend to disk and resume.

---

### Post by akand074 on 2010-04-20
Karmic is terrible at resuming from suspense. I haven't used Lucid Lynx yet but I know people who have and they said the suspend/resume is great now one said even better than Windows. I believe the full release is out in 9 days so you could just get the beta and do the updates or wait for the full release but I think your problems should go away in the new version. Not sure about how to fix it now though.

---

### Post by Craigwell on 2010-04-20
akand074:

I hope that will work if nothing else does - upgrading that is. 

As I say the most frustrating elements of the situation, and what leads me to believe it can be resolved:

1) The system is still functional upon resume, the secondary display works, and even without the secondary display, i can exit to terminal, and enter commands, even if I can't see what i'm doing. 

2) When I execute the reboot command, the garble disappears and is replaced by the ubuntu logo. This to me is an indicator that there must be a way to reinitialize the display somehow.

Worst case, I wait for lucid and try, but I also don't want to install that right away if I don't need to..... 

Thanks again

---

