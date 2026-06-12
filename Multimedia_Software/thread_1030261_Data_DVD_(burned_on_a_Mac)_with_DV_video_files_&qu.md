---
title: "Data DVD (burned on a Mac) with DV video files: &quot;Cannot mount volume&quot; - solution..?"
date: 2009-01-04
forum: Multimedia Software
---

### Post by indiworks on 2009-01-04
A self-burned (on a Mac) DVD with DV video files that I need to access under Ubuntu 8.10 for video editing refuses to show up on the desktop:

"Cannot mount volume.

Invalid mount option when attempting to mount the volume (name of DVD)."

After a while another error message comes up:

"Unable to mount (name of DVD)

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I tested the DVD on my old (and half broken) iMac G5 under OS X 10.3.9 and there it works, I can view the individual DV files, copy them to the Mac desktop etc.

How can I access/copy the files from this data DVD on my Ubuntu 8.10 PC?

Thanks!

---

### Post by indiworks on 2009-01-06
I can't solve this problem but I think it is a bug that has been reported first about two years ago and that is still there in 8.10:

"Setting an invalid mount point can make a removable media inaccessible"

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668)

The DVDs I got have a "/" in the (rather long) disk name and I'm guessing this is what causes the problem. Users in the launchpad discussion above mention all sorts of possible workarounds (though none of them sound too reassuring if you are new to Linux like me).

(Strangely I also can't burn the disk's content on my iMac with another name, so I just asked for new DVDs with short names and no "/" in the disk name.)

**If you are working with Mac users let them know: keep DVD names short and don't use "/"** - the Mac will open it but Ubuntu unfortunately will not... (I even went back from 8.10 to 8.04 to see if this fixes the problem - it did not...)

Hope this info helps other video editors who try to go open-source and this bug gets finally fixed!

---

