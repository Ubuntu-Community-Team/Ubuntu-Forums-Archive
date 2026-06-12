---
title: "Seperate X-screen suddenly misses minimize, close etc. -buttons on windows"
date: 2011-05-01
forum: Multimedia Software
---

### Post by Esso on 2011-05-01
I did a clean install of 11.04 and I have  experienced that my separate X-screen does not have the program-name bar with the minimize, close-buttons etc. It's my third monitor is a separate X and it does not really work since I cant close  programs, maximize windows or move them around. I cant even write anything on it. The first two monitors work great as one X-screen, just as they did in 10.10.
Any ideas?

Ubuntu Classic, no Unity.
Two monitors (one X) on a ATI HD6970
One monitor (the X-screen that doesn't work properly) on a ATI HD4870

An example:
[IMG]http://i56.tinypic.com/34j23r7.png[/IMG]
And another one:
[IMG]http://i56.tinypic.com/27y9vlt.png[/IMG]

---

### Post by krisofe on 2011-05-01
Hi, 
Your aren't alone in that case...
I have a nvidia (ATI made me pbs when video was speed even in low res HD7700).
With 10.10 like you all was great and all actions were available on TV (on the second of 3 screens but third is disable in configuration  because I've just two displays).
I have a different pointer on my second screen, (a "X") and have same pbs than you : as if second screen was a real slave of the primary in X display separate mode.

I'll next try to install the .sh from the nvidia site as you can try catalyst instead of ubuntu driver one, even if the propriety one was installed by ubuntu.

---

### Post by Esso on 2011-05-02
> **krisofe said:**
> Hi, 
Your aren't alone in that case...
I'll next try to install the .sh from the nvidia site as you can try catalyst instead of ubuntu driver one, even if the propriety one was installed by ubuntu.
I use the 11.4 preview from ATI, which works great really. Found out I actually can watch video on the seperate X, the only problem is that I can't write in the terminal, skype etc. and that the window border is... gone.

---

### Post by lumpenkalle on 2011-05-03
Hey,

I've been doing an upgrade from Ubuntu 10.10 to 11.04 and am experiencing similar issues with the "separate X screen" configuration. I am using the proprietary NVidia Driver for my Geforce GTX460. 

My second display is unresponsive to general keyboard input. This includes regular keyboard shortcuts, e.g., to open terminals.

It is possible to restore a working dual-screen setup by disabling compiz (e.g., "no effects" mode on start-up). So it looks like there is some conflict with the latter. 

Hope this helps at first and gives a hint for further research...

Best

---

### Post by Esso on 2011-05-03
> **lumpenkalle said:**
> Hey,
It is possible to restore a working dual-screen setup by disabling compiz (e.g., "no effects" mode on start-up). So it looks like there is some conflict with the latter. 


Yeah, it works properly in no-effects mode, but then I can't watch video at all, no matter what player I use I only get the sound. =C

---

### Post by lumpenkalle on 2011-05-04
@ESSO: That's truly a pity. Have you tried using the proprietary driver provided by ATI (fglrx)?

---

### Post by estevez on 2011-05-04
Its a known bug. Please report your problems with separate X screen on Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/661450](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/661450) - Support for multiple monitors broken

---

### Post by lumpenkalle on 2011-05-04
I've seen the entry in launchpad, but didn't report anything, because the issue here is the same, but there is no real _new_ information concerning the bug....

---

### Post by Esso on 2011-05-06
> **lumpenkalle said:**
> @ESSO: That's truly a pity. Have you tried using the proprietary driver provided by ATI (fglrx)?
Yes, I do, as I mentioned in the first post! =P :)

> **estevez said:**
> Its a known bug. Please report your problems with separate X screen on Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/661450](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/661450) - Support for multiple monitors broken
Thanks, but don't think this is the same? I don't have unity activated now, and I miss the Window Border. But I've read other places that the multiple monitor support does not work as it should in Natty, so I'm checking for updates every day.:popcorn:

---

### Post by Esso on 2011-05-09
Can get it all to work with
```

metacity --replace

```
But I need to have the command running in the terminal all the time. The problem is that when I have it running the comp sees the first two-monitor X as one X-screen, so when I maximize windows they stretch over both monitors. Also all effects are deactivated. Movies only have sound when I use the command.
Bah!

---

### Post by krisofe on 2011-05-14
Hi,

Like Lumpenkalle I have a GTX460 but problems seem appear with any video card (See Esso post)
Question is how rolling back "just" for this because 10.10 was ok for that (like bluetooth implementation wich is only ok with a "service blueetooh restart" in rc.local).

I don't want do a feedback now because hard video decompression is really good here (vdpau really work fine for Nvidia under mplayer than 10.10 in my case and 20G videos are now so much fuild).

With ATI, cool for Esso because never I could had any fast video
even in VGA ! There were a strange quasi transparent line in half of video when there were acceleration in the movies).

Hope there will be an issue.
Perhaps my error is to test the last release just when i was available.

Do you test a good wine without waiting few months ;-) ?

---

### Post by toolunious on 2011-07-31
> **Esso said:**
> Can get it all to work with
```

metacity --replace

```


This worked for me as well!

> 
But I need to have the command running in the terminal all the time... 

You can avoid this by pressing ALT+F2 and type the command in the "Run Application" window. 

Cheers!

---

### Post by bemused0 on 2011-07-31
Hey -- I found myself in the same boat when looking for an alternative to 3 monitors + xinerama -- I ended up going with twinview + separate x session.

The metacity --replace option disables compiz, I think?

I found an alternative here:
[http://radiac.net/diary/id/1306/](http://radiac.net/diary/id/1306/)

Basically a script to add to your session startup applications:
```

#!/bin/bash
# After upgrading to Ubuntu 11.04, compiz fails to initialise the second screen
# This should sort it out
DISPLAY=:0.0 compiz --replace ccp &
DISPLAY=:0.1 compiz --replace ccp &

```

So far it's working nicely for me  -- Thanks to radiac

---

