---
title: "mythbuntu frontend to older backend"
date: 2009-01-08
forum: Mythbuntu
---

### Post by djb61230 on 2009-01-08
Hi everyone,

I'm a mythtv veteran (knoppmyth) but am thinking of trying mythbuntu.  I'm adding a new frontend to my system but unfortunately the older kernel with my 2-year old knoppmyth doesn't properly run the ethernet on the motherboard.  (I run diskless frontends in our home).

I've booted a 8.10 Ubuntu live CD and of course no ethernet problems.  So I was wondering if mythbuntu could be installed on this new frontend (I'll add a drive instead of booting over the network) and be able to talk to my current backend.

Of course my backend is old, as it's .20-fixes.  Any possibility a version of mythbuntu can talk to it?

It's really just a short term fix as I will be building a new backend in the near future.  I really wanted to wait until .22 was released so I could get a stable HD-PVR system going.  But also am interested in playing with mythbuntu, so doing this quick fix would get my feet wet with mythbuntu.

TIA.

Doug

---

### Post by newlinux on 2009-01-08
I think there's a protocol change and I'm sure there's a difference in DB schemas between .20 and .21, which is what 8.10 will run. So I don't think it will work very well. In fact if you put a .21 frontend on your system and connect it to your .20, it will try and update the DB schema and screw up your .20 system (this happened to me, and I wasn't even trying to connect it to my old .20 backend - it found it and tried to update it on its own).

---

### Post by klc5555 on 2009-01-09
> **djb61230 said:**
> Hi everyone,

I'm a mythtv veteran (knoppmyth) but am thinking of trying mythbuntu.  I'm adding a new frontend to my system but unfortunately the older kernel with my 2-year old knoppmyth doesn't properly run the ethernet on the motherboard.  (I run diskless frontends in our home).

I've booted a 8.10 Ubuntu live CD and of course no ethernet problems.  So I was wondering if mythbuntu could be installed on this new frontend (I'll add a drive instead of booting over the network) and be able to talk to my current backend.

Of course my backend is old, as it's .20-fixes.  Any possibility a version of mythbuntu can talk to it?

It's really just a short term fix as I will be building a new backend in the near future.  I really wanted to wait until .22 was released so I could get a stable HD-PVR system going.  But also am interested in playing with mythbuntu, so doing this quick fix would get my feet wet with mythbuntu.

TIA.

Doug


If the Knopp-myth box is running Myth 0.20.2, (that is, something of around the vintage of R5F27) then Mythbuntu 7.10 should work on your frontends. I think Myth 0.20 ran protocol 30, 0.20.2 runs protocol 31, and 0.21 (packaged with Mythbuntu 8.04 and 8.10) runs protocol 40. By design, mixing Mythtv versions fails with the dreaded protocol mismatch error.    

Cheers! :)

---

### Post by newlinux on 2009-01-09
Sorry I didn't mention the older version of mythbuntu - I was thinking it was something about 8.10 that you needed to have your ethernet working. Hopefully 7.10 works for your ethernet as well...

---

### Post by djb61230 on 2009-01-15
Thanks for the help guys.

I ended up installing ubuntu 8.10 and then compiling my SVN checked out version of myth .20.2-fixes that I had on the knoppmyth backend.

It all went pretty smoothly.  A few things like using g++ 4.1 instead of the more recent 4.3.  Configuring xine (I use that for DVD and video) for pulseaudio.  Just have to get the remote working (should receive the irblaster receiver in the mail today) and it will be good to go.

Soon I'll be building the new backend and will try mythbuntu 8.10 on that, exercising the diskless frontend feature.  Hopefully I can figure out importing my older database and getting it updated properly at that point.

Thanks again for your help..

---

