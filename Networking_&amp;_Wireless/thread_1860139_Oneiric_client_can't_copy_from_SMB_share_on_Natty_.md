---
title: "Oneiric client can't copy from SMB share on Natty server. Natty client could."
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by kwaanens on 2011-10-14
I have a server running Natty. I'm sharing the music on that server by right click > "Sharing options" (and that's it, no fiddling with conf-files, etc) and then using Nautilus on the client to browse through and copy. I could even remove files and dirs on the server using the client.

I upgraded the client to Oneiric, and now I can no longer copy from the server. All right click options are greyed out. I can't either write to the shared dirs on the server.
Nothing has changed on the server.

Any pointers?

---

### Post by collisionystm on 2011-10-14
Is your share password protected? You might need to take the entry out of your 'key ring' and connect again entering your credentials.

---

### Post by kwaanens on 2011-10-14
> **collisionystm said:**
> Is your share password protected? You might need to take the entry out of your 'key ring' and connect again entering your credentials.

I'm still able to browse it (and even play music directly from the server), so I would think that this wouldn't matter.
Anyway, I tried deleting any keys on my "key chain" and was asked for it again when I logged in on the server again. No dice, unfortunately :(

---

