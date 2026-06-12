---
title: "Sansa Fuze mp3 player open with?"
date: 2016-09-07
forum: Multimedia Software
---

### Post by marjnap on 2016-09-07
Ubuntu Studio 16.04 64bit
Sansa Fuze v1.02.31A

I have an old Sansa Fuze that mounts with no issue on my Ubuntu 12.04. I'm now dual booting with 16.04 to move everything over to the new OS. However, on the 16.04 the mp3 player mounts, but it pops up the open with dialog box. I tried choosing file manager, but I don't see any of the folders on the mp3 player. I have attached the open with dialog box and the lsusb
[ATTACH=CONFIG]271023[/ATTACH]
[ATTACH=CONFIG]271024[/ATTACH]

---

### Post by marjnap on 2016-09-07
I tried to add a folder to the mp3 player and it said I didn't have permissions. Therefore I looked at the permission and I didn't have access to /media/usrname I took owership with sudo chown -R username /media/username. I hope that doesn't bite me in the ass later.

---

