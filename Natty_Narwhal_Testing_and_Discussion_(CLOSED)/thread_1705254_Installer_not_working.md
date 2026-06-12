---
title: "Installer not working"
date: 2011-03-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Michaelg14 on 2011-03-11
I seem to be unable to install natty from a daily image.  I have tried 4 or 5 images without being able to complete an install.  The last few have hung on the second page "Preparing to install Ubuntu" 

The last successful install was in January.  Would someone like to comment on this?  I can't be the only poor slob who can't install an OS.

---

### Post by cariboo on 2011-03-12
You seem to be suffering from the same bug, as the rest of us. Bug #[lpbug]730209[/lpbug] Add your me too.

---

### Post by mc4man on 2011-03-12
The daily's have been hit or miss here for several weeks. If you don't wish to wait for a good one (march 9 worked here, march 10 didn't, ect.) then the A3 iso should be good (you'll have quite a number of updates but they should go ok.

[http://cdimage.ubuntu.com/releases/natty/alpha-3/](http://cdimage.ubuntu.com/releases/natty/alpha-3/)

---

### Post by meanpt on 2011-03-12
I'm running the alfa 3 iso but want to try a later daily build cause for some days now the ubuntu software center can't run, not even after this night updates. Moreover what's the point in producing faulty daily builds?

---

### Post by coolbrook on 2011-03-12
I finally got it installed this morning.

I downloaded the image for the alternate CD from the daily folder.  I have very old hardware on the system from which I'm typing.  I had to log in with the Ubuntu Classic Desktop session with "no effects".  I've since installed LXDE.  Pretty slow, so far.  I'll be looking into the matters of the high CPU usage reported by the system monitor.

---

### Post by sgage on 2011-03-12
> **Michaelg14 said:**
> I seem to be unable to install natty from a daily image.  I have tried 4 or 5 images without being able to complete an install.  The last few have hung on the second page "Preparing to install Ubuntu" 

The last successful install was in January.  Would someone like to comment on this?  I can't be the only poor slob who can't install an OS.

I had that exact same issue. I found that by booting to the Live Desktop, running gparted, deleting the partition I had set up to use for natty and re-creating it, and THEN firing up the installer, I got past that "preparing to install" phase, and all went as planned.

Also, sometimes I have found that natty does not like to be installed from a USB key, but will install from an actual CD. But sometimes it WILL install from a USB key. I can't figure it out...

---

### Post by Michaelg14 on 2011-03-12
I will try the gparted idea, otherwise I guess I will put in the January image that works and do a ton of updates.

Thanks all

---

### Post by MadCow108 on 2011-03-12
there seem to be some problems when certain filesystems are present:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/729556](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/729556)

my installer hangs in following cases:
lvm
truecrypt ntfs
btfs

removing those makes it work.

---

### Post by ubuntu27 on 2011-03-12
I had the same problem using the DesktopCD (Live CD).

If you want to install Ubuntu Natty now, use Alternate CD instead:

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)


Just make sure your are connected to Internet using ethernet

---

### Post by KrazyPenguin on 2011-03-12
When I tried to install Alpha3, it didn;t work off of a live usb, so I download the alternate cd and put it on usb and installed that way.

---

### Post by kansasnoob on 2011-03-12
For some odd reason I've not encountered the same exact problem ...... but I do know that the UI is undergoing major changes due to this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

Basically the "dumb" buttons have gone away and we'll soon see the return of "install to the largest continuous free space".

But I don't think this problem is related ........... or is it?

---

### Post by VMC on 2011-03-12
The hint on how to get the Livecd ISO installed is found on **_[post #12]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/730209/comments/12")_** of the bug report.

I used an external hard drive. Added a swap and ext4 partition. It completed without errors.
I use partclone and was going to restore it that way, but used gparted instead.

I needed to shrink the partition and then copied from external to internal.
Then I needed to edit fstab to reflect the old swap I use for the other distros.
You need to unplug the internal  drive or change the UUID.

---

