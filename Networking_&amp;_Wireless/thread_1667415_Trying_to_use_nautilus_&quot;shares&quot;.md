---
title: "Trying to use nautilus &quot;shares&quot;"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by ridetheteapot on 2011-01-14
Ok, what I am trying to do is share a folder with the "share" properties in nautilus.
*The folder had a few subfolders and a few symlinks.*
The share is readonly with guest access(as set up by the nautilus properties window).
It successfully shares the folder and subfolders, **but does not share the symlinked folders** (I should mention the symlinks are to other devices, but same owners).

Nautilus is using samba to share, so I checked my ~/.samba/smb.conf and added
```
follow symlinks = yes
wide symlinks = yes
```
....also noting that there was no actual entry for the share here... this did not help me.

It turns out the shares are generated in */var/lib/samba/usershares/*
so i added the link permissions to the file there (which looks like a regular samba share), and still no luck.
What am i missing here?

---

### Post by quixote on 2011-01-15
Have you tried sharing the "off-device" folders on the devices where they're located? Linux (and unix) are quite strict about doing things across filesystems (and directories on a different device are officially on another filesystem).  I'm not sure whether sharing the way you're doing it is one of the not-allowed actions, but it's worth checking to make sure that's not the problem.  (If it is, your only choice is to do the sharing on the device that has the folders.)

---

### Post by ridetheteapot on 2011-01-16
I'm not seeing anything about samba not handling this correctly, and I would think there would be some kind of warning in the documentation for "wide links" if that was the case.

I tried just putting in some symlinks to same-device folders - these didn't show either. (I should specify that I'm not seeing the symlinks at all on the client, it's not "access denied".)

I am just going to try a normal ~/.smb/smb.conf and forget about nautilus-share for now...

---

### Post by quixote on 2011-01-16
Sometimes all that happens is nothing.  No warnings, no snippy messages.  You're right, though.  If there's a way you can do it, don't waste time on nautilus.

---

### Post by ridetheteapot on 2011-01-18
ok, i just uninstalled nautilus-shares, and samba is working fine.

Some things to note are you definitely can share across devices with wide links/symlinks (and you won't need to add any non-browseable shares to make this happen). might be worth mentioning that samba uses user nobody (uid=65534) as guest.

Also as a security precaution wide links can not be used with unix extensions (which are on by default), and unix extensions must be turned off in the global section, not per share. (I am curious if you could use wide links and unix extensions on read-only shares, or rather why you can't).

finally, i'm not sure why nautilus-shares was not working correctly (but i think i only ever tried "unix extensions = no" in my ~/.smb/smb.conf global, while currently i am only using /etc/smb.conf, and have it there... i should have tried it like that with nautilus-shares set-up). its a single user machine- so i don't care.

__.o0o.___quick_update__.o0o.___
did a clean upgrade to 10.10 on that machine (got my first ssd), and since it was already installed- i tried again with 'unix exts = no' in both smb.conf globals - still was no use- so i really dunno what is up

---

