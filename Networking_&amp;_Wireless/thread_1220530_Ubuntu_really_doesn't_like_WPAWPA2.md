---
title: "Ubuntu really doesn't like WPA/WPA2?"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by MrCode on 2009-07-22
Hi, all.  I know I've already discussed the Netgear WN111 in another [thread]("http://ubuntuforums.org/showthread.php?t=1209027&highlight=can%27t+connect+local+home+router"), but the information then was a little fuzzy.  Now I think I have a little bit better understanding of what's going on.

I'm trying to get a Netgear WN111 USB wireless adapter to work with Ubuntu 9.04.  It *really* doesn't seem to like WPA/WPA2 networks, I guess, because I can't connect to my home router, wich is encrypted with WPA2.  It connects with WEP, but I (and others in my family) don't want to use WEP because it's quite easily hacked.  

I have the Windows drivers installed with ndiswrapper, and the adapter works fine.  Is it maybe that Ubuntu just doesn't fully support WPA/2 yet?  I have this problem even in the LiveCD...

If this is the case, I hope that Ubuntu will fully support WPA/2 in the next release...

Is there anything I can do in the meantime?

Also, no amount of re-installing the ndiswrapper drivers helps.  And the connection is *sometimes* successful, but more often isn't.  And when it is, the connection will drop after an inconsistent amount of time, but the nm-applet will say that I'm still connected.

---

### Post by MrCode on 2009-07-22
bump to keep thread alive...these forums update rather quickly.

---

### Post by MrCode on 2009-07-23
bump plz help?

---

### Post by t0mppa on 2009-07-23
Just because your thread falls off the top of the forum doesn't mean it's not getting read, so a little patience goes a long way. Bumping it on an hourly basis really is more like spamming and it's often the threads with 0 replies that get more views than the ones with numerous bumps, as having replies is usually a sign of a work in progress.

Ubuntu can handle WPA and WPA2 perfectly well, I believe most of the regulars that are on wireless here use either one.

I had a similar issue when I tried ndiswrapper a while back and pretty much the only solution offered was that the Windows drivers were so old that they couldn't handle WPA/WPA2. Of course, when I grabbed newer ones for the card, ndiswrapper refused to work with them at all. Got tired of fighting with it and swapped back to a native Linux driver and my wireless started working properly again.

So, your options are to wait for someone with more experience to answer and provide a solution or find out if there's a native driver for your adapter as well. In the mean time, you could consult our good friend Google like the [comprehensive ndiswrapper troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847") in the sticky section points out, as the answers tend to be out there, in case someone else with the same adapter has run into the same trouble.

---

