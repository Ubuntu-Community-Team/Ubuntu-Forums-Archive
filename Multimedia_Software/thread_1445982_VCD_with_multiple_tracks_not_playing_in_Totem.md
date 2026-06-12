---
title: "VCD with multiple tracks not playing in Totem"
date: 2010-04-03
forum: Multimedia Software
---

### Post by cong06 on 2010-04-03
I'm trying to get Totem to play VCD's. There are many complaints about this not working, but since they're all really old and dealing with different problems, it's hard to tell if this is an issue with me, or with the totem package.

When I put a VCD in the computer, I expect it to pop up, (as it does) and prompt me to open the CD with Totem (which it does).
When Totem tries to play it, though, it throws this error:
```

An error occurred
Could not open location; you might not have permission to open the file.

```

Interestingly this is the same error I get when I try to play DVDs on a seperate computer with the same ubuntu software.

The CD plays, however. If I click ok, and go to:
Movie > Play Disk '<disk name>'

The problem is:
1) I want it to be automatic, without errors,
2) These VCD's have several tracks and after the first 30 second track, it stops. It won't play any other tracks.

I tried a few other peices of software just to see if other things worked (as I'm looking for user friendly-ness, I doubt the others will be a final option):
VLC: (No apparent activity. Disk spins)
gxine: Autoplay input plugin &#8216;VCD&#8217; failed: Check engine output for further details.
Mplayer: Error!: Failed to open vcd://2.

K3b seems to have no problem, but it's not really a media player...

---

### Post by cong06 on 2010-05-21
bump

---

### Post by kiers on 2011-01-03
well, Cong06, you are NOT alone.

I manifest THE EXACT SAME symptoms. VCD goes in, totem pops up, then says "error: can not open location". the VCD only loops the introductory 3 seconds of publishers label then stops. EXACTLY like your problem.

WTF? DOes anything work as advertised in Ubuntu? Did you ever solve the problem?

---

### Post by cong06 on 2011-01-03
> **kiers said:**
> Did you ever solve the problem?

No, I'm still waiting for a solution.
I think there's a bug report posted... I'm just waiting for a solution since there's nothing else I can do.

---

### Post by kiers on 2011-01-04
these are the options i've seen "out there" on google:
1) change the backend on totem from gstreamer to gxine.
2) remove libavutil-extra and install libavutil49,50 etc.
3)try mplayer, vlc etc.

I don't want to do #3 cause WTF, totem shd be able to handle it! it's just a matter of the right codecs. besides i've seen on google others having problems with mplayer, vlc as well. i don't wanna bloat up my system with multiple s/w to do the same thing.

have u tried 1 or 2?

---

### Post by cong06 on 2011-01-07
I actually haven't, and I don't think when I tried I had much luck with VLC but I can't really remember.
Also, I don't have a VCD to test with right now. Did you get it to work with any of those? what happened?

---

### Post by kiers on 2011-01-07
One I forgot (from the googleverse) : Medibuntu.

Apparently Medibuntu is NOT in the given "standard" repository due to license issues. 
(BTW I have now undertood, thanks to this exercise, the difference between "restricted" and non-restricted packages with otherwise the same name! restricted means "restricted LICENSE). THey are still free of cost, but not "GNU" Free!

Did you try adding medibuntu to synaptic package list?

I downloaded w32codecs (with trepidation b/c "w" stands for windoze). will get my VCD and report back.

---

