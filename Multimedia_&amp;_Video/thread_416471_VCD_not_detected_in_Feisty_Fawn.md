---
title: "VCD not detected in Feisty Fawn"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by amitst on 2007-04-21
Hi,

When I put VCD inside my CD/DVD drive the OS freezes for 5 minutes and then comes back to normal. But it doesn't play the CD nor does it mount the CD. I opened the movie player but the CD is not mounted so can't play it.

Any other data CD is mounted properly and is accessible.

Before upgrading to Feisty Fawn I could mount VCD but couldn't play it due to some codec error.

Thanks,
Amit

---

### Post by lingnoi on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/82307](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/82307) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
Sounds like a bug. Is it anything like the one above?

---

### Post by amitst on 2007-04-21
No, I can't even see the directories inside cdrom or any .dat files. So don't have a way to copy them.

---

### Post by kwidzin on 2007-04-21
Same problem here. I think it's a hal bug. :(

---

### Post by shironeko on 2007-04-21
Same problem here. Probably a Bug.

The Cd drive does unmount itself.

---

### Post by Eric_T on 2007-04-23
I have the same problem with VCDs as well. No files in the cdrom directory and the cd drive failes to mount.
There is a bug report about this issue here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106786](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106786)

---

### Post by feistybird on 2007-04-24
same here,  only 'mplayer vcd://[COLOR="DimGray"]x[/COLOR]' works, nothing else plays any of my VCDs.

gxine used to work with my previous 6.10, but not any more after upgraded. I've exactly the same problem as described in the above posts.

also, the CD-ROM icon does not appear on my Desktop after it is automatically mounted, so that I can only  eject the device under Terminal by typing 'eject'

---

### Post by shamim on 2007-04-27
Hi,

Just adding my voice here. 

I have the same problem. But it can mount and play multimedia DVD! (but not the data DVD as before :(  )

My wife is pushing me to go back to edgy eft. The same VCD was running there quite fine!

---

### Post by amitst on 2007-11-28
The problem is resolved for me after upgrading to Gutsy Gibon :)

---

