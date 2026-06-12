---
title: "nuvexport problem"
date: 2010-03-11
forum: Mythbuntu
---

### Post by linuxhippy on 2010-03-11
I am having difficulty using nuvexport as a DVD file on one series that I record.  My pc runs mythbuntu 9.10 and is up to date with aptitude.  The problem series is Star Trek The Next Generation (45 minutes each without commercials).  I am able to transcode 2 other series that I record...Seinfeld and The Cosby Show (20 minutes each without commercials) using nuvexport to DVD.  

Any ideas why 1 show would not transcode when others do?  They are all recorded with the same type of video cards (I have 2 Pinnacle 800i tuner cards).

EDIT:

I just had the same nuvexport problem with a 2 hour show.  What it does is that it starts transcoding and then just stops 2 to 5 minutes into the process.  I can then watch the mpg file for about 10 minutes before it stops.  It looks like the problem is with the length of the program...I cannot transcode shows more then 20 minutes.  Could it be that my P4 3.2 GHz/1 GB RAM pc just cannot handle too much work?

---

### Post by linuxhippy on 2010-03-12
If my myth pc doesn't have the power to transcode these videos, could the live install cd for mythbuntu 9.10 be used on an Athlon64 pc and copy the needed nuv files to an external drive for transcoding on the Athlon64?

---

### Post by SiHa on 2010-03-12
I don't think it's a question of not enough grunt. All machines will hit 100% CPU whilst transcoding, the power of the machine will just dictate how long it takes.

It almost sounds like something is filling up when transcoding the larger files. 

How much RAM / swap do you have?
Where does the temporary file Nuvexport creates go?
How much free space does that have?

Are you sure it's the file length? What happens if you edit one of the longer shows to < 20 mins. 
Are the failing shows off a different channel to the good ones? maybe it's a signal issue and there's junk in the recording that causes nuvexport to bomb.

Sorry - no answers, but those are the things I'd check.

---

### Post by linuxhippy on 2010-03-12
I'm glad you don't think it's my single CPU...wish I had a quad core!  RAM is 1 GB and swap is 2 GB.  The RAM is usually almost full and I'd imagine it is using a lot of swap to transcode.  I have my hard disk partitioned into a couple areas-the larger space is where I put my TV recordings and the smaller area (where the tmp directory is) is on a smaller 10 GB partition.

---

### Post by linuxhippy on 2010-03-13
I tried nuvexport again on a 1 hour show.  This time I opened up top at the same time and watch memory and swap.  Memory went down to 13000k and swap wasn't touched.  My /tmp directory didn't fill up either but nuvexport bombed after 5 1/2 minutes.  

Does mythtv use /tmp for temporary files or is that somewhere else?  I was thinking about making a sym link from the used directory to my 212 GB /recordings directory.

---

### Post by SiHa on 2010-03-15
Anything meaningful in the backend log?

---

