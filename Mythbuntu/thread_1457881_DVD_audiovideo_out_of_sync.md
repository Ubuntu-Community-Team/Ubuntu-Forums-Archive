---
title: "DVD audio/video out of sync"
date: 2010-04-19
forum: Mythbuntu
---

### Post by avelach on 2010-04-19
Hi,

I own a box running Mythbuntu 9.10 amd64 and I'm experiencing the following:

I use to play movies and music in my CD/DVD drive. Most movies work fine but some not. For instance I own a children series in several DVDs and some of them work fine but others are completely out of sync, being video playback slower than the audio. Within the same series there is a DVD which contains chapters than run fine but others not.

The "faulty" DVDs run fine in a Debian box I also own.

I tested the same "faulty" DVDs with MythTV's internal player and also with Xine, VLC and MPlayer (out of MythTV). All of them fail.

I even replaced the ATA drive with a SATA unit to no avail, so I guess it is definitely a software issue.

Any help should be welcome!

Regards

---

### Post by mookie60 on 2010-04-20
ok, I'll take a crack at it.

I've had similar troubles, but not with originals, just archival copies made using Myth.   A copy of a video (on a usb stick) would play fine on any pc (linux or mac), but had audio sync problems when play on my tv (usb input).

Assuming your "faulty" videos are original dvds, I have read that some audio sync problems can result when there isn't enough cpu processing capability.   I can't confirm or deny it, but I can see where it would matter.

If your "faulty" videos are copies, then the problem could be Myth.  I've had numerous problems exactly like this.  I've also read many others posting the problem as well.  Based on some recommendations in this forum I switched to using HandBrake for copying, and the problem went away.  Now my copies play on any device, even the tv's usb input, without sync problems.

Hope this helps,
John

---

### Post by tegwilym on 2010-05-10
I just completed building a Mythbuntu 9.10 box.  All hardware is fast, current and good.  I also noticed a similar problem with dvds. It's almost like the video is a little ahead, or the sound lags behind.  The lips and words don't line up right.
I tired the menu settings to sync things up, but it's just not right, and it's all set to 1.0x or whatever that was to line sound/video up.
Sound is great, 5.1 dolby as it should too. 

Anyone have any clues yet?

---

### Post by larsolav on 2010-05-10
This thread may help: [http://ubuntuforums.org/showthread.php?t=1427336](http://ubuntuforums.org/showthread.php?t=1427336)

Activate Auto Builds here: [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)
and then open up Update Manager and check for updates.
This helped me with my sync problems in 9.10

---

