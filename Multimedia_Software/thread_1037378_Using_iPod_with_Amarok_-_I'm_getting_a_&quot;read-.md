---
title: "Using iPod with Amarok - I'm getting a &quot;read-only&quot; message..."
date: 2009-01-11
forum: Multimedia Software
---

### Post by zachthejones on 2009-01-11
I'm running a pretty fresh install of Intrepid Ibex (gnome), and just got my hands on a used iPod. The guy I got it from had cleaned all the music off, so I thought it would be good to go. I believe it is a gen 5 iPod.

My problem is, when I try to set up Amarok to manage it, I get an error message citing a "read-only" problem. I can navigate to the iPod via Nautilus, but I cannot add files due to the same error message.

I can't find any how-to's or threads concerning this issue. Suggestions anyone?

---

### Post by zachthejones on 2009-01-11
okay, figured out the issue. the iPod was initially used on a Mac and formatted with an HFS+ file system (with journaling enabled). Linux can only read that file system (with journaling enabled).

That said, my wife is using iTunes in windows to reformat the ipod (she plugged it in and it detected the issue right off and prompted her for the reformat). Hopefully this will fix everything. I'll post the results later...

(just so irritated I had to use windows to fix something...)

---

### Post by Rhemat on 2009-08-15
I am having the same issue.  My brothers sent me my iPod with an iBook that I used iTunes to upload to it, but that iBook died a while ago, and since I don't have a Windows system, I can't update my iPod.  Could I use WINE to update my iPod?

---

### Post by zachthejones on 2009-08-16
um, maybe, it's worth a shot. There are a lot of issues with running iTunes in Wine, though. If that doesn't work I'd suggest just trying to find a friend with windows who would help ya out. Other than that, I'm not too sure...that's just the quick and easy way I found....

---

### Post by Rhemat on 2009-11-09
My friend formatted my iPod, and I have been using Amarok to add music and playlists on it.  I haven't been able to add album art, but I haven't really tried yet.  You'll need to add transcode (I think it is spelled differently), and support for AAC, but it should work.  I hope this helps you.

---

### Post by tacantara on 2009-11-09
> **zachthejones said:**
> um, maybe, it's worth a shot. There are a lot of issues with running iTunes in Wine, though. If that doesn't work I'd suggest just trying to find a friend with windows who would help ya out. Other than that, I'm not too sure...that's just the quick and easy way I found....

Wine just isn't a viable option for iTunes.  I've had to resort to running it in a Windows virtual machine.  I've had success in the past using Banshee to sync an iPod Classic.  Banshee will do the album art, etc., almost as well as iTunes can.  You might want to give Banshee a try.

---

