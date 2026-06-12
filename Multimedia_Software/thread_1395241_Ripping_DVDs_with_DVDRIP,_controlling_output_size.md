---
title: "Ripping DVDs with DVD::RIP, controlling output size"
date: 2010-01-31
forum: Multimedia Software
---

### Post by beastrace91 on 2010-01-31
Howdy All,

So I am attempting to rip my collection of DVDs to media files and I am using the program "dvdrip" from the reopos to do so. The only thing is that when I tell it to rip it is creating two different video files (one that is 1gig and another that is around 800megs) from a single 43min video clip - how can I get this down to under 1gig per episode and make sure it is in a single file?

Regards,
~Jeff

---

### Post by MartyBuntu on 2010-01-31
To rip DVD's to an .AVI container, I use AcidRip. It's in the repositories. You can manually adjust the file size, depending of course on quality.

---

### Post by SuperSonic4 on 2010-01-31
> **beastrace91 said:**
> Howdy All,

So I am attempting to rip my collection of DVDs to media files and I am using the program "dvdrip" from the reopos to do so. The only thing is that when I tell it to rip it is creating two different video files (one that is 1gig and another that is around 800megs) from a single 43min video clip - how can I get this down to under 1gig per episode and make sure it is in a single file?

Regards,
~Jeff

I don't use dvdrip so I can't tell you properly. Best thing I suggest is to look around in the menus.

My favourite is handbrake CLI and k9copy

---

### Post by beastrace91 on 2010-01-31
> **SuperSonic4 said:**
> k9copy

I just found that one on Google - using it now. I like it.

~Jeff

---

### Post by hemimaniac on 2010-01-31
acid rip is great for speed and quality, just an FYI if you want to "one-up" the finished product over acidrip, try Handbrake, tho not in the repos, it is free and open source, also imo cue set up is easier and more intuitive

---

### Post by beastrace91 on 2010-02-01
I've been using both Acidrip and K9copy for the last day now and I like both of them however I am having different issues with each. K9copy randomly starts segfaulting on after a few hours of usage - the odd thing is restarting my system causes it to start working just fine again for another couple of hours (loging out and loging back in does not fix it, has to be a full reboot).

Acidrip is what I have been using, due to the issue it has on my system is far less troublesome. When I tell it to start my current queue and it brings up the progress window the only information it displays is the "Time encoded:" and the percentage progress at the top. All the other sections (Chapter, Estimated filesize, ect) are left a 0.

Ideas on either of these issues?
~Jeff

---

### Post by tobemem on 2010-04-28
No idea on Acidrip and K9copy issues, but I would suggest you another application: ANDREW ([http://tobemem.memebot.com]("http://tobemem.memebot.com/")).

Use PREF_FILE_MODE=mb in the configuration file if you need a single file with a target size other than the one of a CD.

---

