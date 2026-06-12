---
title: "Can't play imported CD on separate frontend"
date: 2009-11-18
forum: Mythbuntu
---

### Post by plantschi35 on 2009-11-18
Version 9.10 with Mythtv 0.22
1x Backend / Frontend
1x only Frontend

I can't play importet CD's on my separate frontend. On the backend with frontend I can play the importet Tracks. But on my separate frontend I can see the List of the tracks, but cannot play them.
It's the first time I configure a system like that. I want to have all files on my backend but access to it on 2 frontends. After Installation of the seperate frontend there is no directory for musicfiles in the general settings for music. 
I don't know what I need to konfigure on the frontend or backend to stream the music to my frontend

---

### Post by gslug79 on 2009-11-20
You need to share the backend's music directory by NFS (or Samba) and mount it on the frontend. The directory containing music files must be the same on both the backend and the frontend, so assuming it is /var/lib/mythtv/music on the backend, the share must be mounted as /var/lib/mythtv/music on the frontend.

---

