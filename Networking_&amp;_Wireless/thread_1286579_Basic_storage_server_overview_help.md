---
title: "Basic storage server overview help"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by Amblikai on 2009-10-09
Hi everyone, i have 3 machines. Let's call them cupboard, bedroom and living-room. 
I want cupboard to be an always on storage server which can be seen by the other 2 whenever they are on.

I previously used NFS for this when i only had 2 machines. But it was flaky. Is there a better way?

Also, cupboard has 3 500GB drives in it. How do i get the NFS to see the combination of the 3 drives as one directory. Is this what LVM is for?

Thanks in advance.
Kai.

p.s. I'm not an expert but its been around 10 years since i used a non *nix OS so i'm no Newb! Thanks!

---

### Post by Iowan on 2009-10-09
Just my opinion...
NFS is still the logical choice for a *nix system.
LVM sounds right - but dunno if it can be "retrofit".

---

### Post by Amblikai on 2009-10-09
It's ok, i don't really need it to be retrofitted as such. One of the drives is blank and the others aren't too full. I can move the contents onto the blank drive and create the volume with the other 2. Then i can move the data back onto the volume and add the third drive. 

I think! I'm sure the above is possible.

I'll look into it. Thanks for your help. I was hoping that someone would say NFS is still the way to go! I was just beginning to get comfortable with it!

Might do a write up of the steps involved. Couldn't find anything in my search.

Thanks again.
Kai.

---

### Post by Iowan on 2009-10-09
**dmizer** has a [link ]("http://ubuntuforums.org/showthread.php?t=249889")in his sig for NFS (and a couple on FTP and Samba if you'd care to experiment). There's also [this]("https://help.ubuntu.com/community/SettingUpNFSHowTo") help page for NFS setup.

---

### Post by Amblikai on 2009-10-12
Thanks, I'm looking into LVM at the moment, once i have that set up i'll get the NFS ready. I already have experience with NFS so shouldn't be a problem.

Thanks again.
Kai.

---

