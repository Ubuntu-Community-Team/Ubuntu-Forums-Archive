---
title: "CD drive not unmounting properly?"
date: 2008-11-26
forum: Multimedia Software
---

### Post by stevelt on 2008-11-26
Hi all, 

I have a problem with CD/DVD use on intrepid.

Whenever I put a CD or DVD into the drive, then later decide to swap to another disk, the desktop applications still see the old disk, despite having right-clicked the icon, and done "unmount volume", then pressed eject, or just right-clicked "eject"

cat /proc/mounts does not show the old disk mounted, and the disk physically ejects OK.

The problems arise when (for example) :

- I listen to or rip an audio CD
- Then I eject the audio CD & put a DVD in to play.  VLC (and Places->CD) still thinks the audio disk is present & won't play the DVD

Or
- Play a DVD, then eject it.
- Some time later decide to burn a CD.  Brassero/k3b don't think there is a blank disk in the drive despite inserting one.

Any ideas how to debug this?

Many thanks

---

### Post by ToFue on 2011-01-24
<bump>

I've experienced this in Natty as well.  For me it seems to happen on commercial dvd's; upon inserting dvd the disk 'mounts' and reads contents, then apparently a disconnect occurs. I try to access the files or run in movie player, and get "could not read from resource" error.   The file contents remain cached & the system thinks the disk is still mounted even after I manually eject the dvd through the hardware (not using any software unmount). In other words, with no disk in the player ubuntu still thinks it is mounted and offers interaction..

I'm uncertain if it's due to gstreamer or other mount peripherals... but definitely annoying and hindering.

---

### Post by mc4man on 2011-01-24
> I've experienced this in Natty as well
This thread is over 2 years old and unlikely to be your issue(s) (you seem to have 2
There were some issues with ejecting and or umounting optical disks, somewhat resolved though there is a longtime bug still open.
Atm there is no longer an unmount option by default in nautilus, on some systems you can just use the drives eject button, more commonly you need to eject thru nautilus (r. click > eject or click on an eject icon.

You should post your issue in the natty forum
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

---

### Post by ToFue on 2011-01-24
My apologies- I've incorrectly reported as natty. [click *this* post for explanation if curious.](http://ubuntuforums.org/showthread.php?t=1674999) the distro is 10.10;  As well, I was quick to liken the similarities of my issue to what the OP described.

I stumbled on this two-year old unanswered post, and haven't been fortunate to acquire a link to anything similar post amid the other hundred or so that the filter didn't actually filter out. Thank you though, I can now investigate this as two separate issues. Would you by chance know the bug report number?

Thanks

---

### Post by mc4man on 2011-01-24
Now that I think back the bug was that the eject button on the drive wouldn't work, this is going back to 9.04 or 9.10

The correlation is that what i noticed, (and i'm sure others), was that when using just the eject button on the drive, while the disk would now  be ejected, many times the mount would be left. And if so this could cause issues when the next disk was inserted

I think this started in either in karmic or certainly lucid and I believe maverick (can ck.), it's doing it right now on natty 
(though IIRC on some hardware the mount may  not remain
I'm not sure if I filed or saw filed a bug on that, I've taken to ejecting  thru nautilus (mouse click), recollect some response about just use the r.click or click on eject button in places or some players

If you do a r. click on the icon > eject does it eject and unmount?

---

