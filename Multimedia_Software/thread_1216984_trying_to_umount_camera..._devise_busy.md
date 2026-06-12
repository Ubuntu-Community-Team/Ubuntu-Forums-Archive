---
title: "trying to umount camera... devise busy"
date: 2009-07-18
forum: Multimedia Software
---

### Post by eudemonis on 2009-07-18
Ok, I'm trying to umount my camera. I get the message 

umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

I fuser -m the device to see what's keeping it busy, I get this:

/dev/sda1:            3449rce  3461rce  3555rce  3556rce  3562rce  3564rce  3576rce  3579rce  3585rce  3595rce  3600rce  3659rce  3660rce  3661rce  3663rce  3666rce  3668rce  3671rce  3672rce  3674rce  3676rce  3678rce  3679rce  3681rce  3693rce  3694rce  3695rce  3697rce  3701rce  3706rce  3716rce  3740rce  3743rce  3746rce  3749rce  3752rce  3759rce  3831rce  3833rce  3836rce  3841rce  3843rce  3849rce  3877rce  3885rce  3906rce  3911rce  3933rce  3936rce  3938rce  3948rce  3982rce  4308rce  6147rce  6149rce

Can someone explain me what kinds of files are these and how can I kill em...

I tried fuser -k command but it doesn't seem to work...

---

### Post by geoffjay on 2009-07-18
you should be able to unmount the device using the lazy option of umount -
$ sudo umount -l /dev/'whatever the camera id is'

but in your post you've got 'umount: /: device is busy.' did you try to umount root?

---

