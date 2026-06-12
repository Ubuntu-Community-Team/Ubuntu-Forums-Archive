---
title: "Copying files via Wireless; XP -&gt; Ubuntu"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by kayoti on 2009-02-24
I am copying some pictures and videos on my Wireless N from an XP Machine (NTFS) to my Intrepid install (ext3).  The files are copying correctly, but when I browse to them on Intrepid, they all have locked permissions, so I am unable to change the filenames and such.

I double-checked the files original permissions on XP, and they are set as Archive.

Is this an issue with the communication b/t the two filesystems, or am I missing a specific step here?

Thanks!

---

### Post by cariboo on 2009-02-24
Are you copying the files in your home directory? 

I just had a look at a directory of picture that i transfered from a computer running XP to my server running Intrepid, all the files are owned by nobody and only nobody can edit the file names.

I would suggest changing ownership to your username. Open an Applications-->Accessories-->Terminal and type:

```
sudo chown -R user:user /path/to/files
```

Jim

---

### Post by kayoti on 2009-02-26
Jim, I am not copying the files into my Home directory.  Instead, I am pushing them to a second harddrive that I've mounted here:  /nas2/pictures and ~/video.

I changed the ownership to my username using your code and that worked.

But when I copy new files, I have the same problem again and have to enter the code to gain ownership.  Is there a way to give my username ownership automatically?

Thanks!

---

