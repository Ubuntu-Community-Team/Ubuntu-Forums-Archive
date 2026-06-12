---
title: "DVD not being read in Feisty"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by ubukool on 2007-06-22
Hi everyone,

My Feisty distro is not reading data DVDs.  There's a lot of activity for a few mins, and then it stops and there's no DVD icon on the desktop.

Can anyone suggest a way to solve this problem?

Thanks for your help.

BTW, it works fine in Windows XP :(

---

### Post by ubukool on 2007-06-22
Hi ubukool, this is ubukool answering your own question!!  #-o lol!

For anyone who might be having the same problem, I found an answer on another thread.

To solve the problem, go into terminal and type:

sudo mount /dev/cdrom /media/cdrom

This force mounts the drive.   You won't get an icon on the desktop, but if you go into /media/cdrom0, you can read the folders and files on the disc.  Also, it's good to report that since they were music files, Amarok was also able to read them too after doing this. :guitar:   Rock on!

I'm not sure why there is a problem in the first place, since it works fine in Windows XP.  I burnt the discs using XP so I wonder if that might be the reason - If I had burnt the data using gnomebaker or something similar perhaps it would have worked naturally.

---

### Post by Das Goat on 2007-06-27
Any luck getting movies to play? Ubuntu doesn't seem to read any movie DVD disk I insert.

---

### Post by OzzyFrank on 2007-06-27
Movie DVDs need codecs, which coz of copyright etc Ubuntu can't include by default. You can install either xine or gstreamer apps and their codecs, or install Automatix (look for their website as I don't think it installs via Synaptic) which actually downloads and installs things like these codecs for you! For encrypted (copy-protected) discs, you'll need to have libdvdcss2 installed (once again, maybe not easily installed via Synaptic, but found easily enough via a Google search). Not sure if Automatix handles the libdvdcss2 codec, but it might do that as well.

---

### Post by compiledkernel on 2007-06-28
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

Just add the proper repos and youll get all you need.

---

### Post by Das Goat on 2007-06-28
> **compiledkernel said:**
> [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

Just add the proper repos and youll get all you need.

Wee! Thanks guys! The link you posted fixed 2/3 of the problem, then I searched in snaptic for libdvdcss2. I had to because I run 64 bit AMD and the commands you posted only refer to 32 bit codex.

But then it worked! Wee!

Oh, another side note, Flash wouldn't install because there are not 64 bit codex :-(

Anyway, I can watch movies now!

Thanks Again!

---

