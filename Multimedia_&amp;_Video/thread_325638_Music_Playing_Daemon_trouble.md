---
title: "Music Playing Daemon trouble"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by Zaggy on 2006-12-26
I'm trying to get mpd to create a database out of files on an usb hdd but it keeps giving me this:

> zaggynl@AMD3200L:~$ sudo mpd --stdout --verbose --create-db
flushing warning messages
done flushing warning messages
setFsCharset: fs charset is: UTF-8
flushing warning messages
done flushing warning messages
explore: attempting to opendir:
explore:
explore: found: MUSIC (MUSIC)
failed to stat MUSIC: Permission denied
removing empty directories from DB
sorting DB
writing DB
zaggynl@AMD3200L:~$


I'm not sure on how to set the permissions, since the usb device gets mounted automatically, and it gets mounted read only since it's an NTFS volume.

---

### Post by Zaggy on 2006-12-26
To elaborate:

-mpd is running using its own user 'mpd'
-I added this user to the plugdev group.
-The configured music dir is /var/lib/mpd/music
-I made a symlink in that dir which symlinks to my NTFS usb drive

---

### Post by blackpuma on 2008-02-03
I have the exact problem here.
The addition of user mpd to group plugdev doesn't seem to change something.
Note also that my external drive if vfat formatted and it's connected via firewire.
It is mounted by haldeamon.

If someone can answer this i would greatly appreciate a post.

---

