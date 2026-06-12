---
title: "Strange MP3 Issue"
date: 2009-03-04
forum: Multimedia Software
---

### Post by liquidypoo on 2009-03-04
I ran into a fairly strange problem today.  After today's update, I restarted my laptop and went along my usual business.  I've never had any trouble with MP3's before this, but now, well...

I open up Amarok and it tells me it doesn't have the right plugin to play MP3 format.  That's odd.  So I try playing an MP3 in Totem Movie Player (basically my fail-safe program to check and see if something's wrong).  Same story there.  I try playing an MP3 music file in Totem, and it tells me "There is no plugin to handle this movie."  Better yet, M4A music files (MP4, whatever you wanna call them) still work perfectly fine.  This is all very confusing.

Can plugins and codecs magically disappear, and is there some way to prevent this from happening?  Also, do I need to just find and reinstall the plugins, or is there something more elaborate I need to do, considering how odd this situation is?

Edit:  Quick update; reinstalling my existing plugins didn't do a single thing.  Would definitely appreciate help here.  Detailed help, too.  I've used Ubuntu for over 2 years now and I still don't know what I'm doing.

---

### Post by whitelinux on 2009-03-04
I would definately try reinstalling the plugins first and see what happens.

Did you install the Gstreamer codec through synaptics?

---

### Post by liquidypoo on 2009-03-04
> **whitelinux said:**
> I would definately try reinstalling the plugins first and see what happens.

Did you install the Gstreamer codec through synaptics?

I'd forgotten about the Gstreamer codecs!  But still, I just reinstalled those, and there's no change.  I'm gonna try restarting my laptop again, maybe I still have to do that.

---

### Post by Lars Stokholm on 2009-03-04
You can track down the changes made during the update from Synaptic. File > History.

---

### Post by liquidypoo on 2009-03-04
Still no change.  Checked out the Synaptic history, there wasn't anything removed that didn't get immediately reinstalled, so no change there.  Only one slight difference I noticed was that gstreamer0.10-plugins-ugly was upgraded, or something.  That was removed, and updated to gstreamer0.10-plugins-ugly (0.10.7-3).  That can't be the problem though, because that was done after I'd first noticed the issue.

Edit:  OH!  Gnome mplayer still likes MP3s!  This is an interesting development.

---

### Post by Lars Stokholm on 2009-03-04
Sure you're not meaning gstreamer0.10-plugins-ugly-multiverse? That update hasn't reached my mirror yet - perhaps I should steer clear of it for a while...

It's not odd that MPlayer still plays mp3s as it uses its own codecs (not gstreamer).

---

### Post by liquidypoo on 2009-03-04
Well, I'm not entirely sure if those are multiverse or not.  What I typed up there in that post, I didn't even type.  I copied and pasted them just to prevent typos.  They don't say multiverse, so I have no clue.

---

### Post by liquidypoo on 2009-03-05
Bumping because I'd like a solution to this issue.

---

### Post by avrilrox on 2009-03-05
Does it not ask you whether you'd like to search for codecs?

---

### Post by mc4man on 2009-03-05
As far as amarok mp3 support is provided solely by libxine1-ffmpeg, maybe try reinstalling. (if amarok is running close and then reopen.

If still no good try going to home folder -> .xine and inside will be a file catalog.cache. If you delete it and then restart amarok it will be rebuilt, may restore mp3 playback if it was somehow corrupted.

---

### Post by liquidypoo on 2009-03-05
It doesn't ask me if I want to search for codecs.

However, while reinstalling that xine library didn't do anything, forcing Amarok to rebuild catalog.cache did the trick!  I dunno how it got corrupted, but thank you for that one.

Edit:  Problem solved thanks to mc4man!

---

