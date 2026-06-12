---
title: "Is it possible to import media from a remote MythFrontend only machine?"
date: 2009-08-24
forum: Mythbuntu
---

### Post by DominicF on 2009-08-24
Hi,

Is it possible to import media such as Music, DVDs and Pictures from a client PC only running a Mythtvfrontend to a master PC running MythtvBackend?  So, that a second client PC running only MythFrontend can access the media which is now stored on the master backend machine?

Thanks.
DominicF

---

### Post by tgm4883 on 2009-08-24
Kinda, but not really. This may be fixed in 0.22 with storage groups for media. 

You will have to share and mount the media directories to other systems, it may work then.

---

### Post by newlinux on 2009-08-24
Yeah, this will only work properly if all systems have the files located in the same directory structure, meaning machined remote from the data will need to have them mounted. This is what I do with all my remote frontends. All media resides on my fileserver (which is not my master backend, but it could be) and all frontend machines have the media mounted in the same places. E.g. on every machine the same media is located in /media/Movies, /media/CDs, etc. and each frontend is configured to look in the same place.

---

### Post by tgm4883 on 2009-08-25
> **newlinux said:**
> Yeah, this will only work properly if all systems have the files located in the same directory structure, meaning machined remote from the data will need to have them mounted. This is what I do with all my remote frontends. All media resides on my fileserver (which is not my master backend, but it could be) and all frontend machines have the media mounted in the same places. E.g. on every machine the same media is located in /media/Movies, /media/CDs, etc. and each frontend is configured to look in the same place.

Yep, thats how I do it too. Should be easier in 0.22 using storage groups

---

