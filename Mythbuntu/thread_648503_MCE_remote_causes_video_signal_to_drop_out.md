---
title: "MCE remote causes video signal to drop out"
date: 2007-12-23
forum: Mythbuntu
---

### Post by mrming on 2007-12-23
Hi all,

I have a weird one here. I'm running MythTV on Ubuntu 7.10 (Gutsy) using the Microsoft USB 2.0 MCE remote (made by Phillips). All was working great until a few days ago when I'm guessing an update must have broken something.

Now whenever I use my remote in mythfrontend the video signal appears to drop out every three to five keypresses. I use an InFocus X1 projector with my setup and every time it happens the screen goes black and the projector goes through it's "setting up image" phase before the image comes back.

When I navigate mythfrontend via VNC with my laptop's keyboard I don't experience the problem, hence my deduction that it must be caused by the remote.

If anyone has any idea what might be causing this, or any ideas on which log files to look at in order to start diagnosing the problem I would be very grateful. I have my relatives coming round for Christmas Day on Tuesday and I'd really like my MythTV setup to be 100% well-behaved.

Cheers,

Phil

---

### Post by mrming on 2007-12-23
I've done a bit more sleuthing on this one, and it appears that multiple keypresses are causing the problem.

Say for example I adjust the volume while a recording is playing back. If I push the volume button quickly, no problem. If I hold the button down the screen goes black and then a few moments later the picture comes back. The volume only drops one notch in mythtv (as repeat is set to 0 on all keys), but I can see from irw that lirc is registering lots of key presses. I don't really know where to go from here so any help would be greatly appeciated...

---

### Post by mrming on 2007-12-24
Okay I've got to the bottom of this one and it turns out that neither MythTV, LIRC or Ubuntu are to blame. Somehow my MCE remote has started interfering with the IR receiver on my projector, so the projector was reseting it's image based on a command from the wrong remote!

Lots of time wasted debugging software but at least I got to the bottom of it in the end.

---

