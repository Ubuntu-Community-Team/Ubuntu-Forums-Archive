---
title: "Can't play audio CDs"
date: 2005-11-28
forum: Multimedia &amp; Video
---

### Post by manobes on 2005-11-28
Hi

It's been a while since I've tried to play audio cds, but something has changed since last I did (among other things, I've upgraded from hoary to breezy).

When I insert an audio CD, KDE attempts to automount it, and fails with an error

"could not read /dev/hdc"

and it attempts to start the cd player, which fails with an error

"
CD ROM read or access error (or no audio disc in drive)

Please make sure you have access permissions to 

/dev/hdc
"

The relevent line from /etc/fstab is

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

If I try to mount the cd, I get

mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error

Does anyone have any ideas?

---

### Post by kairu0 on 2005-11-28
Make sure that your user is a member of the "cdrom" group. This could be your permission problem.

---

### Post by manobes on 2005-11-29
[QUOTE=kairu0]Make sure that your user is a member of the "cdrom" group. This could be your permission problem.[/QUOTE]

Thanks, that worked.  I remember playing audio CDs with this account before, so I'm not sure what changed.  But anyway, it's working now.

---

