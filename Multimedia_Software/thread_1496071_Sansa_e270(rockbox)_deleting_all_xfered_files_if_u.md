---
title: "Sansa e270(rockbox) deleting all xfered files if unplugged"
date: 2010-05-28
forum: Multimedia Software
---

### Post by unc0nn3ct3d on 2010-05-28
This just started happening and I can't fathom why.  If I cue up a bunch files and directories to the mp3 player and then simply unplug it when it is done everything I've transfered is instantly wiped.  It's not like it was even xfered in the first place.  The only way to retain what I xfered over is to sudo umount the device from shell.  

Anybody have any idea why this is happening and what I can do to fix it?

---

### Post by MartyBuntu on 2010-05-28
It's possible the files are still being written when you unplug the device.

---

### Post by unc0nn3ct3d on 2010-05-28
hmm,woudln't that leave me with broken partial files instead of completely erasing them?  For example if I unmount it manually in the middle of a file transfer it will leave the file on teh device but it will be only half there.

---

### Post by MartyBuntu on 2010-05-29
Not necessarily.

Does the Sansa icon appear on your desktop?

---

### Post by unc0nn3ct3d on 2010-08-06
It does while it's plugged in yes

---

### Post by MartyBuntu on 2010-08-06
Try right-clicking the Sansa icon and removing the device from there.

That's what I use.

---

### Post by unc0nn3ct3d on 2010-08-06
Indeed, but what I was after was having the ability to simply unplug it without having to do that.. And it seems like I may have figured it out.. Kind of.. 

If you mount the drive with the 'sync' option on, it will allow you to unplug and retain the data transfered..

Now if I could just get my NTFS drive to auto-mount through HAL with this on I would be set.

---

