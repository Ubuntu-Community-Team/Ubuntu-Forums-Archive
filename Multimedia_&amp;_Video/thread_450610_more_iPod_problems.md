---
title: "more iPod problems"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by strm on 2007-05-21
I have a **6th generation U2 30gb iPod** and i am using **gtkpod**, the first time i plugged in the iPod ubuntu automatically mounted it on in *~/Desktop/THE SPOD*, I could view the directory structure and play the files on it with both xmms and mplayer. Then I opened gtkpod and followed the instructions found here [http://www.ubuntux.org/node/147/](http://www.ubuntux.org/node/147/), setting the mount directory to *~/Desktop/THE SPOD* and editing /etc/fstab accordingly.

After that didn't work, I right clicked on the icon created on my desktop (THE SPOD) and changed its mount point to /mount/ipod and changed the setting accordingly in gtkpod.
Now whenever I plug in the iPod, I get an error saying:
```

Cannot mount volume.
Unable to mount the volume 'THE SPOD'.
Details:
mount_point cannot contain the following characters:
newline, G_DIR_SEPARATOR (usually /).

```

Finally, when I run gtkpod, none of the files from the iPod show up, however I can "write" mp3 files to it, in quotes because, they dont actually show up on the iPod when I unplug it, but when I plug it back in to my laptop, those mp3 files are the only ones that show up.

Any help would be appreciated, thanks.


**EDIT**
I finally got it to work myself, i changed the mount point to /media/ipodtest, changed gtkpod preferences again, and made sure /etc/fstab had the right device in it (ie, the large partition of the iPod as listed in fdisk -l).

---

### Post by reclusivemonkey on 2007-05-21
Thanks for posting back and telling us how you fixed it.

FYI, you might want to try GPixPod for your pictures, and you can also sync contacts and calendars from Evolution with the appropriate plugins.

If your album art doesn't work, you also might want to check out this thread;

[http://ubuntuforums.org/showthread.php?t=430350](http://ubuntuforums.org/showthread.php?t=430350)

---

