---
title: "Using MythTV DVR with Uverse Reciever"
date: 2010-01-13
forum: Mythbuntu
---

### Post by poke4christ on 2010-01-13
I've got Uverse and I'm curious if it's possible to grab the IPTV stream off the network yet?  I've seen some talk about this possibility, but my searching has turned up no solution.  Is the only way to get TV from a Uverse receiver just a normal card like a Standard Hauppauge or HD PVR + Blaster?

If we could grab the stream off the network, we'd still need the blaster to control it, but we could get around a lot of other issues.

---

### Post by poke4christ on 2010-01-14
So it appears no one has any clues on this.  Well, I might have to give it a whirl myself.  I'll post back in here if I figure anything out, but I'm not sure I've got the skills at the moment to make it happen.  I'm guessing I'll probably have to do some packet sniffing.

---

### Post by bcg30506 on 2010-01-15
I've been looking into uVerse but haven't talked myself into it yet.  How do you like it?  Is the quality good?  How's their DVR?  I hear it is Windows-based. (yuck!)

Just curious why you need MythTV with uVerse since they give you a DVR?  I know I like to archive stuff onto DVDs so I would need a way to get recorded shows from the uVerse DVR into MythTV.  I think the HD-PVR would meet that need and keep it in HD, though I'm very unsure about the logistic details of actually making that happen.

Sorry to not answer your question.  I didn't mean to hijack your thread.

---

### Post by poke4christ on 2010-01-20
The quality is actually kinda crapy, but I was coming from OTA transmission which is AMAZING.  It looks horrible on sports (fast moving), but I think that ESPN might already compress their stream a little bit too much and be the real cause. Haven't had enough comparison with others.  Other than that and the lag on the reciever I like it pretty well.  So far my IP address has stayed solid and I'm a big fan of that for remoting in :).

As for the reason for the thread, it looks like the IP Multicast traffic is encrypted.  I was able to tune to it by find the IP and port of the Multicast in a sniffing program.  Then, I opened it with VLC (if you want the instructions, I can be more specific).  It showed some stream information, but it couldn't diplay any video or audio.  :( Looks like our only recourse is the HD-PVR.

---

### Post by poke4christ on 2010-01-20
Forgot your second question.  As for why I would want it, the Uverse DVR isn't free.  It's $15 if you are on U100 or lower.  Even then, it's really being factored into your service cost and not free.  That's something that always pisses me off about providers.

Even then, I want the freedom to be able to use my own equipment and be in control.  I'm a Tech Nerd and like so many of them, I'm a control freak and don't want to be in control.  Their DVRs are locked down with DRM, have limited storage space, and limited capability. In addition, I don't think there is really a way to get your recordings off of the DVR. Even if there is, I think many of them haf the broadcast flag that prevents it from happening.

---

### Post by bcg30506 on 2010-01-20
Thanks for the incredibly detailed answers!  The reports of the HD-PVR are very good so it sounds like a reasonable solution.  For now we are sticking with cable and using the HDHomeRun for free HD.  The HDHR quality and ease of use is amazing!  I'll probably go uVerse once we decide to get paid HD service now that I know it will work with MythTV via the HD-PVR.

---

