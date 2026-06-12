---
title: "Ipod integration in Ubuntu"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by Xixor5000 on 2007-11-13
I am having a problem with rythembox/gtkpod/amarok closing as soon as i plug in my iopd to the usb.  After some research I have come to the conclusion that the autoupdate program which is already on the hard drive of my ipod is causing this problem.  My ipod is formatted from windows itunes so I think i may need to reformat my ipod in windows in order to start from scratch

Is this a wise idea to fix the problem and if so can anyone point me towards a tutorial which would help me reformat my ipod from scratch and then update my rythembox linrary onto the newly reformatted ipod?  Thanks,

---

### Post by Xixor5000 on 2007-11-13
So I ran rhythmbox from terminal too see what kind of error it was and it spit this out:

** (rhythmbox:10718): CRITICAL **: ipod_parse_artwork_db: assertion `itdb' failed

(rhythmbox:10718): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault (core dumped)

Any ideas?

---

### Post by Xixor5000 on 2007-11-14
So my roomate who is also running the same version of 7.10 ubuntu tried my ipod and it has the exact same error on his computer although he has no problems with his ipod

any help would be greatly appreciated

---

