---
title: "MythVideo playing from NAS hangs"
date: 2010-01-19
forum: Mythbuntu
---

### Post by DerylFox on 2010-01-19
I recently setup a NAS with 1.5TB of space in it.  It wasn't long until I decided to extend the videos that I hosted on Myth from just movies to TV series using that space.  I wanted to be able to continue to utilize the spin down property of the NAS to conserve power so I set up autofs to mount the NAS' samba share when someone tried to watch one of the shows.  

However, the first time someone tries to access the NAS it has to spin up.  This seems to result in the frontend hanging with the "Please wait..." text on screen.  But if I first access the folder, causing it to mount, then try to watch a show it all works just fine.

What would the community recommend to resolve this issue?  Thanks.

---

### Post by kja999 on 2010-01-19
Hi,

Not very constructive I know, but I have a similar setup (mythbox on lan and a QNAP nas mounting with autofs), and it plays videos with no issues. Likewise all my music is on there.

Both the apps, mythvideo and mythmusic pause while the spin-up happens, but continue ok afterwards ...

Maybe its a disk speed thing ? I have 2x1Tb Seagate's, which spin up in turn .. may take up to a couple of seconds.

---

### Post by DerylFox on 2010-01-19
Yeah, at first I wondered if it would be the spin up.  But after 10 minutes of just watching the black screen with no response from the system except for Ctrl-Escape I decided it was stuck.  

Since yours works without problems I wonder if it does take longer for the NAS to spin up than yours and so I ask if anyone knows a way to increase the time the internal player waits for I/O when opening a file?

---

