---
title: "Need Intel Poulsbo (GMA500) lpia (or i386) Kernel!"
date: 2009-12-15
forum: Multimedia Software
---

### Post by LifeTheHound on 2009-12-15
The methods in the wikis fall flat for the lpia architecture (the only architecture worth having on the netbooks/nettops/MIDs/Vaio P that use it) in the latest karmic kernel 2.6.31-16. 

This is simply ridiculous. But it's okay. :) I know it wasn't meant to be supported by karmic, and I know it's not exactly your fault or anyone's fault really (except Intel). 

But there used to be some custom kernels floating around. All I'm looking for is a custom lpia kernel (preferably in a deb or ppa) of a Poulsbo-enabled kernel. Then none of that nonsense and mucking around with scripts and downloading all these random packages and special xorg tweaks or any of that nonsense needs to be worked through (only to fail on my Vaio P, mind you).

Any link to a ppa or deb with the lpia (aw heck, even i386...) kernel with pre-built/pre-configured Poulsbo/GMA500 support would be soooo useful. 

Thanks so much. I know I can count on the community. 

If you know of someone who can help but just isn't reading this thread, could you please *bring it to their attention* or let me know their contact information so I can ask directly? I know this is a problem with forums, and I understand this. For my part, I'll keep bumping until I get some response. :) Thank you!

---

### Post by mikewhatever on 2009-12-16
I really don't know about lpia. It's an experimental architecture, with builds for Jaunty and Karmic, but I am not aware of any other distro using it. Why do you have to use lpia? If you want something working out of the box, try Mandriva One or JoliCloud.

---

### Post by snowpine on 2009-12-16
Get rid of lpia (Canonical has dropped support for it) and check out [this thread]("http://ubuntuforums.org/showthread.php?t=1229345").

---

### Post by LifeTheHound on 2009-12-17
I doubt simply "getting rid of" lpia will help--like I said, normal i386 software works just fine with it, and I've never run into a single problem before this one (and I see reports of this problem floating around the net with normal i386). 

I'm concerned since the repos linked to in that thread are dealing with Jaunty, and the last update to that particular thread was early October, way before the current -16 kernel. 

Is it possible for someone to patch the kernel with those modules, then package it in a deb for me and other users running into these problems? I'm fine with editing the xorg file manually of course, but the other steps don't seem to function properly. 

Also, just as a minor aside, lpia seems fairly active in the ports tree, and does give the best performance on the 3 netbooks I've tried it on. Many ppa's compile with 386, amd64, and lpia as a pretty default set of options. Sure there's no official standalone lpia cd-image (besides in ports), but it seems pretty widespread and packages are being actively updated, including those in ppa's, nonetheless. 

I'll take *any* patched kernel at this point, including i386.

---

### Post by LifeTheHound on 2009-12-18
Anything? Anyone?

---

### Post by LifeTheHound on 2009-12-23
Not sure how the rules apply to bumping a thread, but...

bump. :)

---

### Post by LifeTheHound on 2009-12-23
bump

All I need is a kernel (lpia OR i386) with built-in poulsbo for karmic...

---

### Post by LifeTheHound on 2010-01-14
bump

Anyone know if poulsbo works in Lucid? If so I might just upgrade to today's alpha 2 (or the kernel thereof).

---

