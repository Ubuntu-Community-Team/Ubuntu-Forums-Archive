---
title: "Rockbox/iPod help"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by onero on 2007-07-10
I just installed Rockbox on my iPod Nano, and everything went pretty well. At least until I deleted the contents of the Music folder (in the iPod Control folder). That was ok, I thought I'd just restore the files from my Trash folder ... but when I tried plugging in my iPod again, it was be mounted as read-only every time, so I couldn't restore my files >.<  

Also, another concern is that even though the files were deleted, the Free Space in the iPod wasn't updated, so it reflects something like 195 MB free space even though it's almost empty. The reason why I unplugged / replugged my iPod was because it wouldn't let me copy back my files initially because there was not enough free space, according to it.

Anyway, can anyone help me to somehow restore my data? Even reverting the iPod as it was (back to the orignal iPod firmware) would be a big help, since I have backups of my files. Thanks!


EDIT: OK, I guess I figured out why the free space is still the same; the iPod Trash is still in the iPod itself, in a hidden folder ^^ But I can't cut/paste it because it's read-only. So now my question is, how can I mount it so that the disk is writeable?

---

### Post by onero on 2007-07-10
OK, my iPod works correctly in Windows, I just tried it out with my laptop ^^ And I upgraded the firmware, so it doesn't start up as Rockbox anymore. But when I plug it in Ubuntu, it still mounts as read only :(

I'm thinking there might be residual settings either in the iPod or somewhere in my system that's making it mount as read only, but I'm not too familiar with mounting / unmounting or messing with fstab, so could anyone help me with this? Please? :) Thanks!

---

### Post by Matakoo on 2007-07-10
> **onero said:**
> I'm thinking there might be residual settings either in the iPod or somewhere in my system that's making it mount as read only, but I'm not too familiar with mounting / unmounting or messing with fstab, so could anyone help me with this? Please? :) Thanks!

Try:

sudo mount -o remount,rw /media/ipod (or wherever it is mounted,
you can find where by just using mount on its own)

---

### Post by onero on 2007-07-11
Hi, I tried remounting, still no go. I also popped the Ubuntu Live CD into my laptop to see if the ipod would mount correctly there, but all the files were still read-only, so I guess I can assume it's not something in my ubuntu installatiion but something in the ipod itself. 

Are there any hidden settings, etc., that I could change?

Also, I don't know if it's important, but when in Windows, all the files have the "read-only" property filled out (and I can't change it, even when I try to modify it). However, it doesn't seem to affect file operations in Windows, as the ipod works normally in Windows.

---

### Post by onero on 2007-07-11
Yay! It's working now. I don't know why, but I think the issue was that there were some corrupted files / directories in the ipod, which was the reason the ipod was locked. I deleted all the corrupted directories using Rockbox (couldn't delete them in Windows), and now I can write to the ipod again :)

---

