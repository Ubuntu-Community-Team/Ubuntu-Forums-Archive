---
title: "Audio CD Won't Show Up -- Feisty"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by llanitedave on 2007-10-25
My DVD-rom drive will mount data cds just fine,but it can't read an audio cd.  I can't get them to show up as a play list on the desktop, nor can Amarok find them.

It used to work, and I'm not sure what happened.

In my KDE system settings under the "Disk & Filesystems" setting, it shows a mount point of /media/cdrom, a Type of iso9660, the Device to be /dev/cdrom, and the status to be "Disabled".

When I try to enable it, the error I get is /dev/cdrom:  no medium found.

Looking in /dev, I see cdrom, which is a link that points to /dev/hda.

And /dev/hda is a block device of size 0.

And here, I'm stuck.

What do I do now?  I don't have a clue.

---

### Post by iank998 on 2007-10-28
I have the same problem in Gutsy.  No idea why it broke (recently) still researching, but nothing obvious in dmesg.

Frustratingly it's only audio cd's that don't work.  Data CD's and DVD's both work as expected.

---

