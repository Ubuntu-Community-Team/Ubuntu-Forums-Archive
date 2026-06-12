---
title: "Keeping diskless frontend updated?"
date: 2011-02-01
forum: Mythbuntu
---

### Post by raptorjr on 2011-02-01
I'm building MythTV from source, master version, because i need to apply some patches and like to look around and learn more about the code.

But now i have added another frontend that is diskless and booting using PXE. What would be the best way to keep the diskless frontend updated with the same version that i have on my backend?

I'm thinking something about updating the overlay so whenever i start the frontend it is already up to date. And i dont need to start it just to update it every time i compile a new version. But how to do that the best way?

---

### Post by nickrout on 2011-02-02
you need to install the debs you are creating in your main install, into the chroot environment that the frontend boots from.

---

### Post by raptorjr on 2011-02-03
I'm not creating any debs. I'm just using make install when i have downloaded new code from master, or made any changes myself. Don't know how to make debs but that is the best way? Is there any guide to make debs, can they use the makefile so i get all the necessary things?

---

### Post by nickrout on 2011-02-03
> **raptorjr said:**
> I'm not creating any debs. I'm just using make install when i have downloaded new code from master, or made any changes myself. Don't know how to make debs but that is the best way? Is there any guide to make debs, can they use the makefile so i get all the necessary things?

Well in that case you aren't really using mythbuntu and your problem probably belongs elsewhere :)

However you could simply compile it again in your chroot.

---

