---
title: "mythvideo can only read files in parent directory"
date: 2010-08-21
forum: Mythbuntu
---

### Post by bigbodytad on 2010-08-21
Just switched from mythdora to mythbuntu and am loving it so much more...except for mythvideo.

When looking in media library - videos, I am able to see files in the parent directory (videos) but not files in folders (for instance videos/Adventures of Pete and Pete).  How could I enable it to scan/view subdirectories containing other video 
files?

---

### Post by winewood on 2010-08-21
You have to have extensions for those files defined with a player that can play them.  
 
For example, say you are unable to see .m2ts files.  Once you define a player for it, say 'mplayer' they will appear.

---

### Post by nickrout on 2010-08-23
more likely an ownership/permissions issue.

---

### Post by bigbodytad on 2010-08-24
hte permissions solved it! my user was authorized, but not mythtv. 

thanks!

---

