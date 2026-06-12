---
title: "Audacious plays but no window after tried to change skin"
date: 2010-10-29
forum: Multimedia Software
---

### Post by orbital on 2010-10-29
Ubuntu 10.10, I tried to switch to another skin for Audacious but after this the program window won't show, yet music plays ok.

I tried uninstalling Audacious and installed it once again but it didn't help. How can I get the program window to show?

Maybe there is a way to **completely** uninstall Audacious and get the default settings back somehow?

---

### Post by ully-mick on 2010-11-12
I had this, and the way I fixed it was to :-
go to home folder, under view "show hidden files"
go to ".config" folder then open the audacious folder, rename "config" file in the audacious folder to "config-bak" then close window. 
(thats the config file in the audacious folder)
launch audacious and the default window will appear. go to file - preferences - plugins. under the general tab tick status icon.
close window
under view tick "show player"
now you can change your skin.

---

### Post by orbital on 2010-11-14
Thank you this was exactly what I needed to do.

---

### Post by LisaO on 2010-11-18
> **ully-mick said:**
> I had this, and the way I fixed it was to :-


Thank you very much. This one has been worrying me since switching to Ubuntu 10.10  :D

---

### Post by obaino on 2011-01-18
> **ully-mick said:**
> I had this, and the way I fixed it ...

Thanks for your answer :-)

---

### Post by obaino on 2011-01-18
> **ully-mick said:**
> I had this, and the way I fixed it ...

Thanks for your answer :-)

---

### Post by themacmeister on 2011-09-15
Many thanks -- this one had nearly beaten me!

fully solved on second attempt (deleted entire audacious config folder first, but I think audacious was still running). Working fine now!

---

