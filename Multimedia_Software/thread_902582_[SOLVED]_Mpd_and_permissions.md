---
title: "[SOLVED] Mpd and permissions"
date: 2008-08-27
forum: Multimedia Software
---

### Post by Nonno Bassotto on 2008-08-27
I have been using mpd on my pc for a while. Now it stopped working. It is a computer I only use when at my parents' home, so it may have stopped working after upgrading to Hardy, or it may not, I'm not sure.

I have created a symbolic link inside /var/lib/mpd/music, pointing to my music folder, which is on a NTFS drive. Now
```

sudo mpd --create-db

```
has no effect whatsoever. The database is empty. I tried changing the permissions of my music folder, but it seems I can't. Could this be related to NTFS? How can I make mpd work again?

---

### Post by Raffles10 on 2008-08-27
By default NTFS drives are mounted in read only mode, to auto mount your drives in read/write mode at boot you can use the [NTFS Configuration Tool]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G"):

sudo apt-get install ntfs-config

You should then be able to build your database without sudo. Although this doesn't explain why it was working then stopped.

---

### Post by Nonno Bassotto on 2008-08-27
The drive is read-write by default (since Hardy I think), I have no problem writing to it. Still no mpd working. If I launch mpd without root permissions I get
```

cannot setgid for user "mpd" at line 35: Operation not permitted

```

---

### Post by Nonno Bassotto on 2008-08-27
Ok, fixed. I'll mention how in case someone reads this again. When run as root, mpd drops user privileges and runs as a user specified in the file /etc/mpd.conf or ~/.mpdconf
The default was "mpd"; in order to make it work with NTFS I had to change this to "root".

---

