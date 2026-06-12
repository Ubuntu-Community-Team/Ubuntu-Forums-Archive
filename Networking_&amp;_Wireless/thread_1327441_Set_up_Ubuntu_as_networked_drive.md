---
title: "Set up Ubuntu as networked drive?"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by vinay427 on 2009-11-15
Hey,

I have been searching all over for the past week for a solution but haven't found anything.  I have a PS3, Mac, XP, and two 9.10 computers all connected to a network.  I wanted to use one of the Ubuntu computers as a networked media server sort of thing.  I can set up Mediatomb with my PS3 flawlessly, but is there a way to make the hard drive show up on every computer as if it's a network attached hard drive like the [Iomega Home Media Network Drive]("http://go.iomega.com/section?secid=40639")?  That is a bit too expensive for me as of now so I would like to find a cheaper (free) option.  What do you think is the best way I can emulate many of the features on that?

Thanks,
vinay427

---

### Post by vinay427 on 2009-11-17
Bump.  Sorry...

---

### Post by movieman on 2009-11-17
You can set up Samba or NFS, no idea whether all your computers can access those.

---

### Post by vinay427 on 2009-11-17
> **movieman said:**
> You can set up Samba or NFS, no idea whether all your computers can access those.

But do either of those actually appear as a hard drive on a network or as a computer?  From what I've seen I think computer.  Is there anything that can make the computer appear as a hard drive?

---

### Post by movieman on 2009-11-18
Well, if you create a Samba share for the disk you want other PCs to access then both Windows and Linux should be able to see it on the network.

---

### Post by vinay427 on 2009-11-25
> **movieman said:**
> Well, if you create a Samba share for the disk you want other PCs to access then both Windows and Linux should be able to see it on the network.

Ok, thanks a lot!  I'll have to try that soon.

---

