---
title: "mythvideo 0.22 - what storage format should videos use?"
date: 2009-10-29
forum: Mythbuntu
---

### Post by Dewey_Oxberger on 2009-10-29
I'm testing 9.10RC/0.22.  I've copied a "library" of about 10 videos that don't work in 9.04/0.21 to the 9.10/0.22 system.

Quote the 0.22 wiki about the new Storage Group use in mythvideo:

>  Disadvantages

    * ISO/VIDEO_TS Playback does not presently work in Storage Groups (Fix planned for .23) 


Can't play ISO or VIDEO_TS...  Dang, that's my entire library.

What formats should I have ripped to to make a 0.22 library (and how should I have done it)?

(I'm guessing no storage groups for me until 0.23...)

---

### Post by uncle hammy on 2009-10-29
Yep, the Wiki is very clear that Storage Groups are not complete.  I had to migrate my MythVideo setup back to the "old fashioned" way too.

---

### Post by larsolav on 2009-10-29
> **uncle hammy said:**
> Yep, the Wiki is very clear that Storage Groups are not complete.  I had to migrate my MythVideo setup back to the "old fashioned" way too.

Doh! My kids' videos are all in ISO or VIDEO_TS files. Mr. Uncle, how did you migrate the MythVideo setup back to the "old fashioned" way?

Thanks!

---

### Post by xinix on 2009-10-29
This link might be handy for some set-up hints:

[http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide](http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide)

---

### Post by slamhound on 2009-10-29
I think (though someone can correct me if I am wrong) that to use the old way, you just make sure there are no directories listed under storage groups (and you have paths to the appropriate directories in the old locations).  I had to disable storage groups for a while when there was a bug using the internal player for .vob files.  I remember just removing the lines from the storage group setup (in backend setup) and then it worked the old way.

---

### Post by uncle hammy on 2009-10-29
Yep, just don't set any storage groups, and make sure you have your paths listed in Setup>Media Settings>Video Settings>General

---

### Post by larsolav on 2009-10-29
Thanks xinix, slamhound, and uncle hammy!

---

### Post by Dewey_Oxberger on 2009-10-29
I nuked the Storage Groups as well (nice job that 0.22 saved the names of them so I could easily recreate them).

Still, I'm not sure what I was supposed to rip them as.  I normally just let a windows box rip them via samba to the backend.  Was I supposed to transcode them?

---

### Post by mrand on 2009-10-29
Just a fly-by posting: there seems to be a lot of confusion regarding this.  The short story is that storage groups and local directories are not mutually exclusive.  You can use BOTH:

[http://www.gossamer-threads.com/lists/mythtv/users/404731#404731](http://www.gossamer-threads.com/lists/mythtv/users/404731#404731)

[INDENT]Marc[/INDENT]

---

### Post by uncle hammy on 2009-10-29
That's some good info mrand.  I think the issue with it is, while Storage Groups and Local Directories may play well together as systems, they don't play well together if they point to the same folder.  If they are the same folder, then Storage Groups gets the priority, which puts me right back into the boat I was trying to get out of.

Since I don't want to have directories littered all over my system just to support both Storage Groups and Local Directories, it's just plain easier to stick with Local Directories until Storage Groups have matured and can support VIDEO_TS/ISO.

---

### Post by nickrout on 2009-10-29
The problem with isos and storage groups is that a storage group does not give access to the raw disk block device, which one of the libraries (I think its libdvdcss) needs.

---

### Post by fenian on 2009-10-29
I like x264 with the .mkv container for transcoding dvd.If you are using windows Irecommend the program "Automkv" [here is a guide]("http://www.afterdawn.com/guides/archive/encode_dvd_avc_automkv.cfm")for Automkv.If you are usin Linux I recommend Handbrake.

---

### Post by xinix on 2009-10-29
I have some discs ripped as iso files.  They would not play nice with  'Storage Groups' and the 'local files' pointed to the same folder.  Myth would actually try to play the physical disc drive instead.  These files play just fine after I removed the directory from 'storage groups'.

---

