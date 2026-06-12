---
title: "Music CD crashes sound-juicer, rhythmbox"
date: 2010-03-09
forum: Multimedia Software
---

### Post by ryank76nz on 2010-03-09
I have some seemingly interrelated issues with music CDs that I can't find threads about.

Music CDs don't mount, they just spin for a bit then sit there.

While a music CD is in the tray, sound juicer (Audio CD extractor) dies with a Segmentation fault. Rhythmbox dies too with this fault:

```
** (rhythmbox:3526): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3526): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Segmentation fault

```

This only happens while a music CD is in the tray. All other times, the programs run fine. 

Any help appreciated!

---

### Post by ryank76nz on 2010-03-12
*bump*

---

### Post by ryank76nz on 2010-03-13
This forum isn't what it was for help...

---

### Post by ryank76nz on 2010-03-16
Hello? Anything I can post to help?

---

### Post by ryank76nz on 2010-03-23
*bump* I will keep bumping... someone must be able to suggest some direction I could take on this.

---

### Post by ERockwell on 2010-03-24
Could this be bug 501207 ? I just installed Mint on an old laptop, and have same / similar problem.

---

### Post by ryank76nz on 2010-04-24
True, looks like it's not even fixed in the next release. Sigh

---

### Post by MgFrobozz on 2010-05-02
Same problem here; it starts up ok if there's nothing in the tray, but if there's a music-cd in the tray, flashes the program window and then dies with the message below.

It's too bad that grip was removed; that was a reliable, easy-to-use ripper.

```

(sound-juicer:4862): GStreamer-CRITICAL **: gst_value_deserialize_enum: assertion `en' failed
Segmentation fault

> uname -a
Linux aratas 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux
> lsb_release -rc
Release:	9.10
Codename:	karmic

```

---

### Post by Mphill102 on 2010-05-06
The same thing is happening to Me. I have done a fresh install of 10.04. Rhythmbox will shut down as soon as I put a audio cd in.Take out the cd and it will work. I can get VLC to play the cd.

---

