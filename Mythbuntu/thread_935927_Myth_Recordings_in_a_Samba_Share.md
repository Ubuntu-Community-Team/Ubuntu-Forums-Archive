---
title: "Myth Recordings in a Samba Share?"
date: 2008-10-02
forum: Mythbuntu
---

### Post by Eric Boring on 2008-10-02
Hi,

I've got a combined frontend/backend running on an old machine. Right now I've got 200 Gigabytes of storage on an EIDE drive. I want to add a big drive to this system, but the old machine does not support SATA.

I could get 750 gig in EIDE (I haven't seen any EDIE drives any bigger than that). But I could also add a Terrabyte SATA drive to my file server (which is on a mini-itx box). That would be both cheaper and bigger than EIDE.  

Can I just mount the drive as a share in Mythbuntu and then add the  directory in Mythsetup? And, if anyone else has done, this have you had any performance issues? (I know it will depend on connectivity, etc, but what have you'all experienced?) The two machines are on their own 10/100 switch. I watch on the backend and on a remote frontend sometimes (connected via wireless at around 54 Mbs.)

Thanks for any advice!

-Josh

---

### Post by newlinux on 2008-10-02
I have recorded over the network (100Mbps) on a Samba share and the performance was perfectly fine for SD. HD was fine, a little sluggish when playing back something that was recording and trying to skip around in the recording. But then, this was also a an external USB drive and the recording was also being commflagged. My guess is that if you get good network speeds you'll probably be fine.

What types of recordings are you planning on playing back? Will these be myth recordings or media for mythvideo?

---

### Post by Eric Boring on 2008-10-02
> **newlinux said:**
> 
What types of recordings are you planning on playing back? Will these be myth recordings or media for mythvideo?

Standard Def mythtv recordeings for now. I haven't played with mythvideo much yet.

Thanks for the response!

-Josh

---

