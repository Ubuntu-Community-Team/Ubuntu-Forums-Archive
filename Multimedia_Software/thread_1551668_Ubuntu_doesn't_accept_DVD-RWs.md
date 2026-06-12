---
title: "Ubuntu doesn't accept DVD-RWs"
date: 2010-08-12
forum: Multimedia Software
---

### Post by M4he on 2010-08-12
Dear Ubuntu-community,

there's one major issue left preventing Ubuntu from running flawlessly on my machine.
Ubuntu doesn't recognize DVD-RWs once written on. The problem occurred with my old drive (LG GSA-H55N) as well with my new drive (Samsung SH-S222L).

[LIST]
[*]I'm using Sony DVD-RW (1x-2x speed)
[*]Ubuntu only recognizes *blank* DVD-RWs
[*]once written on - no matter whether written by Brasero or Windows 7 - Ubuntu isn't showing any drive in Nautilus nor in Brasero after putting in the DVD
[*]therefore I can't even erase them
[*]both of the drives as well as the DVD-RWs are working *perfectly fine* on Windows 7 (erasing, writing)
[/LIST]
Please help me. I managed to get all other things working by now. My system is close to perfection and this is the only remaining major issue.

---

### Post by M4he on 2010-08-13
Any idea?

---

### Post by ronnielsen1 on 2010-08-13
I've had issues with Memorex disks. Have you tried a different brand of disks?

---

### Post by ihatetryingtopickaloginna on 2010-08-13
Mine will see them, but they are finalized. Can be read but not written too.

---

### Post by M4he on 2010-08-13
> **ronnielsen1 said:**
> I've had issues with Memorex disks. Have you tried a different brand of disks?

No I didn't so far. The Sony disks are working fine on any computer here running Windows and also on our DVD-Recorder connected to our TV.
So it seems to be an issue of how Ubuntu communicates with the DVD drive since the drive itself can handle those disks (at least under Windows).

---

### Post by Jonie on 2010-08-14
It's actually being fixed. Look at this thread on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/581925](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/581925)

I made an unofficial build of udev (you need just udev package) at my ppa, which is supposed to address this issue.

Can you tell me, is it a DVD-RW disc in restricted overwrite mode? You can find it out by typing

dvd+rw-mediainfo /dev/sr0

---

### Post by M4he on 2010-08-14
> **Jonie said:**
> It's actually being fixed. Look at this thread on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/581925](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/581925)


Nice to hear I'm not the only one with this issue and even better that it's being fixed.
Will this fix still reach Lucid or might we have to wait until Maverick?

> **Jonie said:**
> Can you tell me, is it a DVD-RW disc in restricted overwrite mode? You can find it out by typing

dvd+rw-mediainfo /dev/sr0

Yep, it seems like that's the case:
```
 Mounted Media:         13h, DVD-RW Restricted Overwrite
```Thanks for taking care of the problem!

I always admire such users which are spending their time to help other users with their knowledge and skill regarding Ubuntu and Linux.
Hopefully some day I have enough knowledge to do the same and return the favor to the community...
Until then I've to rely on users like you, whom I'm really grateful to.

---

### Post by Jonie on 2010-08-14
> Nice to hear I'm not the only one with this issue and even better that it's being fixed.
Will this fix still reach Lucid or might we have to wait until Maverick?

I have no idea, maybe? It should be accepted first.

For the time being you can either play with the unsupported build or put the disc back into sequential mode (this is going to wipe all data from the disc!)

```
dvd+rw-format -blank=full /dev/sr0
```

This will make the disc act like sort of a huge CD-RW. Neither arbitrary overwrite nor extending a session will be possible, but multisession will (incompatible with standalone players, though).

There is no such stopgap for DVD+RW until you install the fix.

Note that command line utils like cdrecord or growisofs do work, no matter what the GUI shows.

> I always admire such users which are spending their time to help other users with their knowledge and skill regarding Ubuntu and Linux.
Hopefully some day I have enough knowledge to do the same and return the favor to the community...
Until then I've to rely on users like you, whom I'm really grateful to.

I feel little embarrased now... But you've already started to return your favor, haven't you?

---

### Post by M4he on 2010-08-14
> **Jonie said:**
> 
```
dvd+rw-format -blank=full /dev/sr0
```

That's working like a charm! I just erased my unaccepted DVD-RW with that and voila both Brasero and Nautilus recognize it as a blank one. I just wrote some data on it and it's still working :)
Thank you very much!

Is quick-erasing possible that way too?

> **Jonie said:**
> But you've already started to return your favor, haven't you?
In which way?

---

### Post by Jonie on 2010-08-14
You can just quick blank without the =full optional argument. But this is going to work only if the disc is already in sequential mode. For a formatted (i.e. restricted overwrite) disc you have to apply full blanking (the surface will have no visible "track" then). Quick blank erases just the innermost area and some if not most of the data can still be recovered.

> In which way?

Well, I meant you're part of the community, here, asking questions that may help the others. With a tiny typo that a non-native could be pardoned:))

---

### Post by M4he on 2010-08-14
> **Jonie said:**
> You can just quick blank without the =full optional argument. But this is going to work only if the disc is already in sequential mode. For a formatted (i.e. restricted overwrite) disc you have to apply full blanking (the surface will have no visible "track" then). Quick blank erases just the innermost area and some if not most of the data can still be recovered.

Thanks for the explanation! I'll mark this thread as solved now.

> **Jonie said:**
> Well, I meant you're part of the community, here, asking questions that may help the others. With a tiny typo that a non-native could be pardoned:))

Being part of the community and just asking questions is no big deal in my opinion. Helping others with soft- and hardware-related problems and developing bug fixes for open-source software is what I mean. Ubuntu is built on the open-source community after all...
Contributing to it feels like a duty to me; maybe because I love this OS so much ;)

---

