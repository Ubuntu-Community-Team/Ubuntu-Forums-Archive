---
title: "Best Storage type for recordings?"
date: 2013-03-26
forum: Mythbuntu
---

### Post by drewdin on 2013-03-26
I have a separate drive for my recordings, i currently have it formatted XFS since the recordings are large, is this still the best solution to store my large videos? The drive is a 2T, thanks!

---

### Post by ajgreeny on 2013-03-26
Surely the best format type for that purpose will depend more on how you intend to access those files than the size of them.  However it also will depend on exactly what you mean by "recordings are large";  how large is large?  Fat32 has a file size limit of 4GB but most other likely format types will not be limiting on a 1TB drive, eg ntfs has a file size limit of 16EB, as does ext4, way above the total drive size.

---

### Post by tgm4883 on 2013-03-26
> **ajgreeny said:**
> Surely the best format type for that purpose will depend more on how you intend to access those files than the size of them.  However it also will depend on exactly what you mean by "recordings are large";  how large is large?  Fat32 has a file size limit of 4GB but most other likely format types will not be limiting on a 1TB drive, eg ntfs has a file size limit of 16EB, as does ext4, way above the total drive size.

I'd assume since this is in the Mythbuntu forum, that he plans on using it with MythTV. Large is about 5GB/hour, so a sporting event can be a 20-30GB file.

The default Mythbuntu filesystem type is ext4. I used xfs in the past (pre-ext4) and ext4 once it was released. Currently, I use NFS mounted storage from my NAS.

---

### Post by Ubu_Fester on 2013-03-27
I have a 2TB storage drive for mythbuntu and I'm using ext4.  

I have read in some posts that ext4 is recommended but turn journaling OFF.  I presume that would possibly improve performance (disk I/O would be less?), however, I don't know.

Questions related to ext4/journaling:  1) Is it possible to turn journaling off and how to do that  2) does that indeed improve performance from a purely video storage/DVR POV.

---

### Post by sudodus on 2013-03-27
If you need no Windows access, I'd recommend ext4 as it is. Journaling is good, it decreases the risk to lose data, and it will be fast enough for multimedia. If you need more speed with an external drive, use eSATA or USB3 instead of USB2. (If internal, connect with normal SATA).

---

### Post by drewdin on 2013-03-28
I dont need windows access, and i would prefer to stay away from ntfs.

I read this: [http://www.mythtv.org/wiki/XFS_Filesystem](http://www.mythtv.org/wiki/XFS_Filesystem) from the mythtv website, that's why I originally used XFS in the first place but i haven't seen anyone else use it. I wanted to see what the best option is for recording HD shows, like stated above 5gb per hour can get up to 12gb files. 

So I take it that I should be using ext4? Thanks Guys

---

