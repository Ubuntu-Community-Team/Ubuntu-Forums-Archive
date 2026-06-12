---
title: "Ipod transfers hanging"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by jofobuntu on 2007-10-07
OK, my Ipod is killing me.  It's a 5th-gen white ipod.  I'm running Feisty on an AMD Turion64 laptop.

I can mount my ipod just fine, either manually or automatically.  Once mounted, I can navigate the filesystem, read/write files, etc...  But as soon as I try to use anything to transfer mp3 to the ipod, the program hangs.  It's like it's waiting on a blocking I/O call that never returns.  Not only does the GUI freeze, but not even kill -9 will kill the program.  BUT, as soon as I physically disconnect the ipod, the program resumes just fine. (But of course it complains that the ipod is missing or something...depends on the program).  Sometimes, I don't even get to the point of actually trying a transfer.  Even just reading the Ipod database will hang he program sometimes.

This happens with gtkpod, amarok, exaile.  I may have tried others but after awhile, it all runs together.

I tried floola and gnupod_tools and while they don't hang, they also don't seem to transfer anything.

Things I've tried: 
* I ran dosfsck on the ipod.  It usually finds errors after the forced disconnects.  But even after running it, the above-mentioned problems still happen.
* I've tried downgrading to libgpod1 and an earlier version of gtkpod.  Same results
* I installed RockBox on my ipod, but apparently it piggybacks on Apple's disk mode so that didn't help.
* I used a windows box and completely refreshed the ipod to Factory.  Immediately connected to linux and tried a transfer: same thing.
* I tried using older kernels but I can only go back so far because X won't load anymore on most of them.

I'm really pulling my hair out with this one.  Has anyone seen or heard of this?  I'd really appreciate if someone could point me in the right direction.

Thanks

---

### Post by Daveth on 2007-10-07
is this one of the very new ipods?

If it is, this is of relevence

[http://blogs.guardian.co.uk/technology/2007/09/15/new_ipods_not_ready_for_linux_either_by_design.html](http://blogs.guardian.co.uk/technology/2007/09/15/new_ipods_not_ready_for_linux_either_by_design.html)

though it was cracked over a weekend.

---

### Post by tgalati4 on 2007-10-08
When your ipod is connected, post the output of:

>cat /etc/fstab

and

>cat /etc/mtab

and finally

>dmesg | tail -50

---

