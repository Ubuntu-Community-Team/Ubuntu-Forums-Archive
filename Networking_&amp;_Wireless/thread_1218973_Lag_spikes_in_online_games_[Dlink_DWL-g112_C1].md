---
title: "Lag spikes in online games [Dlink DWL-g112 C1]"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by Gird3r on 2009-07-21
I'm getting crazy, TF2 is my absolutely favorite online game now. And by solving this issue would make my experience much better.

I have nice broadband, and I get NO lag spikes under wired gaming. However, when i'm on wireless. I get the dreaded lag spikes.

Under windows, this was solved by shutting down Windows wireless service thingy, and then starting it again. This got all lag spikes to dissapear. So now I know it's not the fault on the router or my Wireless USB adapter.

Is there a similar solution for ubuntu? 

Info:

Ubuntu 9.04

I'm using the funny little network manager icon. Or what's it called.


DO NOT SUGGSEST GO WIRED. I simply can't.. not my apartment you know.

So, if it was fixed on windows, how do I fix it in ubuntu?

---

### Post by Gird3r on 2009-07-21
bump. :(

---

### Post by Pltinum on 2010-04-22
year late bump.

---

### Post by Crowd Control on 2010-11-30
7 month fresh bump. This literally kills me sometimes. :)

---

### Post by aport on 2011-04-12
I know this is an old thread, but the information about this topic seems to be lacking. I've had this issue for a very long time, and it's never been fixed.

It's a problem with NetworkManager. Probably something to do with background scanning.

Uninstall that crap and install wicd. Problem solved.

edit: Technically it's NOT a problem with NetworkManager, it's a problem with crappy wireless drivers, but Mr. Williams has refused to add an option to disable background scanning... instead he prefers to chide his users, saying that it's their fault for not buying Atheros cards. What a nice guy. The point is that wicd doesn't do background scans when you're **already connected**, so there's no problem.

You can either patch NetworkManager ([http://pastebin.com/dTSEqNxJ](http://pastebin.com/dTSEqNxJ)), use wicd, or buy a brand new wireless card.

---

