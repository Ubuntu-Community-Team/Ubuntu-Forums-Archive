---
title: "Speed/throughput difference between NFS and Samba?"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by JillSwift on 2009-02-01
After moving the last PC on my home network to Ubuntu from Windows XP, I'm looking at using NFS over Samba for local file sharing. The one question I can't seem to answer definitively through searching the forums here:

[LIST]
[*] Is there any significant difference between Samba and NFS so far as throughput/speed especially on sustained transfers between client and server?
[/LIST]
 Running the two in parallel, getting a large file via Samba seems to top out at 7.5 MB/s over my 100Mb/s network, while NFS seems to get all the way to 10.0MB/s - Where this would seem to answer my question, I guess I just want to know if there really is supposed to be a diference or if I made a mess of setting up the Samba shares. :)

---

### Post by jrusso2 on 2009-02-01
NFS is supposed to be faster but part of that is people don't know how to set up samba correctly.  Yours should be much faster then what your getting.

---

### Post by Crafty Kisses on 2009-02-01
As stated above NFS is probably faster if you're just talking about speed. I'd personally prefer Samba, but that's just because I've used Samba. I mean NFS is not going to be all that much faster, but I know it can make a difference in the end, being a little faster can make a big difference.

---

### Post by dmizer on 2009-02-01
NFS is faster because it was developed for Linux. The open source version of Samba was reverse engineered from the Windows closed source version of Samba. Samba is fairly inefficient, and difficult to configure correctly. However, if it IS configured correctly, the speed can be dramatically increased. Still not as fast as NFS will go, and yes the speed difference is noticeable.

---

