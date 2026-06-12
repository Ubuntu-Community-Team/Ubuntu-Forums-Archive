---
title: "System equalization and fullscreen video from democracy (now miro)"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by djrobthaman on 2007-07-24
Hi,

I have two very distinct questions.

1.  Is there a way to have sound equalization (adjust bass, treble, mid, etc) for the system in a "global" mixer/equalizer in feisty?

2.  I was watching fullscreen video in democracy player before I upgraded to miro (I haven't checked to see if the issue is still there, but I'm about to start watching and will post again to say whether it's continuing) and even though I have already edited my xorg.conf as below after some time the screensaver starts running.  When I watch vlc this does not happen, so what should I do to fix this?

Thanks

xorg.conf snippet
```

Section "ServerFlags"
	Option	    "blank time" "0"
	Option	    "standby time" "0"
	Option	    "suspend time" "0"
	Option	    "off time" "0"
EndSection

```

---

### Post by djrobthaman on 2007-07-24
Ok... So, miro seems to have fixed my full screen problem.  But I'd still appreciate any help in figuring out how to have some sort of global equalization for feisty.

Thanks

---

### Post by djrobthaman on 2007-08-15
Hi again....

So I just reinstalled ubuntu and miro and now I'm having the problem with the screensaver again.  I already edited the xorg.conf to have the changes in my earlier post but still after about 10 mins, it goes to screensaver.

Any ideas on how this can get fixed?  

Thanks

---

