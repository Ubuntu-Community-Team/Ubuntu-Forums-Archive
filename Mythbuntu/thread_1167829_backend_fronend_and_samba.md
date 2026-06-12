---
title: "backend fronend and samba"
date: 2009-05-23
forum: Mythbuntu
---

### Post by stevanbt on 2009-05-23
Hi,
I've recently split myth backend onto a separate pc.  The backend has 2 dvbs cards and all recordings, music, videos, digital pictures etc.  The backend uses MythWake to shutdown and startup as required for recordings.  

The backend also responds to wake on lan which is issued by the frontend via /etc/rc.local.  

That all works well, however the music, vidoes and pictures are mounted via samba on the backend.  I had put the mount points in /etc/fstab, but they don't get mounted at boot time (the frontend waits for a long time, I suspect this is because the network isn't up and running or wake on lan hasn't been issued).  So I can't put the mount statement in /etc/rc.local.

Is there a better place to put the mount statement.  I guess I only need to mount the shares when the frontend goes into 'Watch Videos' or 'Listen to Music'.  Is that possible?  Alternatively it would be ok to mount the shares when the frontend connects to the backend.

I can mount the shares via the command line easily enough, but my wife just wants something that works without the need to 'fiddle'.

Thanks in advance, Steve.

---

### Post by ian dobson on 2009-05-23
Hi,

Why not just add the mount command to your /etc/rc.local (this is called after all startup scripts) you can add a sleep XXX then mount bla bla bla.

Regards
Ian Dobson

---

### Post by stevanbt on 2009-05-23
Hi Ian,
Agreed this will work (may take a little time sorting out how long to sleep for), but the majority of the time I don't need the mounts to be there.  So I wondered if there was a way to mount them only when needed, i.e. only when going into 'Listen to Music'?

Thanks, Steve.

---

### Post by ian dobson on 2009-05-23
Hi,

Have a look here [http://www.linux-archive.org/ubuntu-user/268157-auto-mount-cifs-partition-via-samba.html](http://www.linux-archive.org/ubuntu-user/268157-auto-mount-cifs-partition-via-samba.html) post number 3 about autofs.

I don't use autofs but it might do it for you.


Regards
Ian Dobson

---

### Post by stevanbt on 2009-05-25
Hi Ian,
Fantastic that worked!

Thanks, Steve.

---

