---
title: "Help with Network NAS Settings Please/"
date: 2011-03-06
forum: Mythbuntu
---

### Post by pgs3223 on 2011-03-06
Can anybody help a complete MythTV Novice?

I have installed MythTV on Ubuntu 10.10 from the repositories and it is working, so far so good!

What  I would appreciate some help with is how to tell it to play music,  video and pictures from a Netgear ReadyNASDuo over my home network  without copying the files locally to the PC running MythTV.

Can anybody help me with the appropriate MythTV front/backend settings for playing files over a home network please?

---

### Post by tgm4883 on 2011-03-06
> **pgs3223 said:**
> Can anybody help a complete MythTV Novice?

I have installed MythTV on Ubuntu 10.10 from the repositories and it is working, so far so good!

What  I would appreciate some help with is how to tell it to play music,  video and pictures from a Netgear ReadyNASDuo over my home network  without copying the files locally to the PC running MythTV.

Can anybody help me with the appropriate MythTV front/backend settings for playing files over a home network please?

I love the ReadyNAS Duo, I use it here :)

You need to set it up the NAS for NFS. Then mount the different shares via NFS on the backend. Then just create the mythtv storage groups at the same directory you have each of the mounts (pictures, videos, music, etc)

---

### Post by pgs3223 on 2011-03-06
Many thanks!

Any chance you could elabourate, I am new to all to this, a little more help on where I need to go to change the settings and what syntax I need to use would be really helpful.

Best Regards

---

