---
title: "Mother board failed, rebuilt, remounted videos, now fast forward/rewind slow"
date: 2014-12-17
forum: Mythbuntu
---

### Post by num1bryanp2 on 2014-12-17
Hello all,

After a MB failure, I replaced the MB and rebuilt the system (Mythbuntu 14.04.1 frontend 0.27 64amd) and remounted drives containing videos. Now I have discovered the fast forward/rewind of videos are very slow and jump random like in either direction. I read that this can be caused by a corrupted data base not have the right video time saved. 

Also, I had to fetch details for each video after remounting.

Any ideas?

Thanks,
Bryan

---

### Post by aelfric55 on 2014-12-18
Usually this means the seektable for the affected recording is bad and has to be rebuilt. It Take a couple of minutes per recording. Rebuilding the seektable can be done with mythcommflag or with mythtranscode. Sometimes one of these utilities will work on a particular recording, but not the other. So if one utility fails to rebuild the seektable properly, try the other one.

The basic instructions are shown here: [http://www.mythtv.org/wiki/Repairing_the_Seektable](http://www.mythtv.org/wiki/Repairing_the_Seektable)  Test them on a recording known to have a fast-forwarding/rewind issue. If the mythcommflag method works for you, give it preference because it's easier to automate across a large collection of recordings than mythtranscode is.

---

