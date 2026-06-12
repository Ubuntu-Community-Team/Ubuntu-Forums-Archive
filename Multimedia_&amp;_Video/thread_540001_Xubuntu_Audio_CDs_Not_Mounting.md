---
title: "Xubuntu: Audio CDs Not Mounting"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by shoomg on 2007-09-01
I'm new to Xubuntu, so apologies in advance if the answer to this is obvious.

A few days ago I set up my new Xubuntu installation to play audio CDs using XMMS. At that time everything was working:
-- When I inserted an audio CD in the drive, an icon for the drive would appear on the desktop.
-- I had specified in the Thunar file manager that audio CDs should autoplay using XMMS, using the command: /usr/bin/xmms -p /cdrom
-- So when I inserted an audio CD, XMMS was launching and the CD was automatically playing.

Cool. Everything's good.

Except that some time after that it broke. I've been installing and uninstalling various other multimedia applications (installed Audacity and the Gnome multimedia apps; uninstalled Rythmbox, Kaffiene, and the Gnome multimedia apps) and at some point I think something broke this.

Now what I'm seeing is this:
-- When I insert an audio CD in the drive, the icon no longer appears on the desktop.
-- And XMMS no longer automatically launches.
-- If I open XMMS through the Applications menu and try to access the audio CD, the CD won't play.
-- BUT: if I open a command line window and type the command: /usr/bin/xmms -p /cdrom, XMMS does start and the CD does start to play properly. And the sound is fine. And after this point, I can close and reopen XMMS and manually play the CD.
-- However, if I eject the CD and then reinsert it, the original problem returns.

So: audio CDs still work, but only if I start XMMS from a command line.

I checked and Thunar is still set to autoplay audio CDs using XMMS. Since the icon is no longer appearing on the desktop, it seems to me that the problem is not with XMMS or with Thunar's settings.  It seems that the problem is that the operating system is not seeing that an audio CD has been inserted into the drive, so it never even tries to run XMMS, and doesn't put the icon on the desktop. And until I run xmms from the command line, the audio CD seems to be invisible to everything.

So does anyone have any idea of what could have caused my system to stop working properly, and what I need to do to get it back?

Thanks.
Greg

---

### Post by shoomg on 2007-09-01
Some things I should have mentioned in my previous post:

-- I'm using Xubuntu 7.04, Feisty Fawn

-- In the last two days I also installed and set up Samba and pyNeighborhood, to allow the Xubuntu machine and my Windows machines to share folders. One step in the pyNeighborhood setup was to change the permissions on samba's mount and unmount commands:

sudo chmod +s /usr/bin/smbmnt
sudo chmod +s /usr/bin/smbumount

I don't think this could have any effect on the mounting of CD drives, but I thought I should mention it.

---

### Post by shoomg on 2007-09-01
More details about this problem. I no longer think it's a problem with audio cds; I think it's a problem with automatically mounting of any CDs.

Today I inserted a data CD (containing MP3s) and it did not mount automatically either. I could not access the drive until I opened a command line and manually issued a mount command. So it looks like the problem is clear: something in the operating system configuration has changed so that CDs are not being mounted when they're inserted in the drive. But it isn't the setting in Thunar's volume management dialog - that is still set properly.

Any ideas of where I should look?

In case this is of any use, this is the current state of my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8928e7b1-ef4b-4a45-a30f-5fafb170cd08 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=2baacf8d-7a92-4f16-baa8-353f04667e2f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by shoomg on 2007-09-02
I haven't been able to fix this problem, but I did come up with a workaround. I created launcher icons on the desktop for mounting and unmounting CD-ROMs and for playing CDs with XMMS. These issue the same commands that I said above were working from the command line. This is a good enough fix so I'm not looking into this problem any more. But I will check this thread occasionally to see if anyone has an answer. To me it looks like a problem with Thunar's volume management but I don't really know.

---

