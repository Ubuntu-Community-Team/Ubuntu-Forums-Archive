---
title: "Minimal Install: Ubuntu Gutsy server + Mythtv backend"
date: 2007-10-12
forum: Mythbuntu
---

### Post by sgreszcz on 2007-10-12
Hi,

I'm migrating from a Ubuntu-based Mythtv frontend/backend (Dapper) to a separate frontend and backend architecture based on Gutsy.

My backend is low powered, headless server which will just be used to serve files, run Asterisk and Mythtv backend.

I know I need X-Windows to configure Mythtv, but I would like to know the minimal packages that I would need to get mythtv backend running on Ubuntu Gutsy server.

The server is running the OS from flash, so I would like to move the mysql location to the hard drive which will store the media and tv recordings.

Thanks!

---

### Post by superm1 on 2007-10-12
mythtv-backend-master

---

### Post by superm1 on 2007-10-12
Mind you, even though mythbuntu installs X, that may be sufficient for you.

It is rather convenient to have VNC setup already then, so you can run mythtv-setup without having to X forward from your headless box.  Your call though :)

---

### Post by sgreszcz on 2007-10-12
Thanks for the advice.

I checked out the two packages: mythtv-backend and mythtv-backend-master and it seems that they are more or less the same except the mythtv-backend has X, so transcoding and audio.

I am unfamiliar with Mythbuntu.  Is there anywhere I can see what packages are installed for a backend only?

---

### Post by superm1 on 2007-10-12
> **sgreszcz said:**
> Thanks for the advice.

I checked out the two packages: mythtv-backend and mythtv-backend-master and it seems that they are more or less the same except the mythtv-backend has X, so transcoding and audio.

I am unfamiliar with Mythbuntu.  Is there anywhere I can see what packages are installed for a backend only?

Well mythtv-backend-master depends on mythtv-backend :)

Take a look at mythbuntu-desktop.  That will get you all the essentials for mythbuntu, mythtv-backend-master gets added onto that when you choose a primary backend role basically.

---

