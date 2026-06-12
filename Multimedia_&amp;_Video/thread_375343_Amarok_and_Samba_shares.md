---
title: "Amarok and Samba shares"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by GuiGuy on 2007-03-03
I recently moved my music library from my Ubuntu PC to our homes WinXP MCE PC. I had been using Amarok, which I like. 

However, Amarok doesn't want to play music files from a remote (networked) PC- Amorok will start and then shut down without any warning.

I have found a few other posts and notes that suggest that Amarok has issues accessing shared files on remote PCs. Can someone confirm/ advise?

Thanks

---

### Post by SigmundFreud on 2007-03-03
I asked the developers about this, and the reply was "Amarok does not support streaming over an smb share" -- you will have to mount the network drive first and then play using the mounted drive. Irritated me, especially the fact that Amarok crashes when you try to do it anyway.

---

### Post by GuiGuy on 2007-03-03
> **SigmundFreud said:**
> I asked the developers about this, and the reply was "Amarok does not support streaming over an smb share" -- you will have to mount the network drive first and then play using the mounted drive. Irritated me, especially the fact that Amarok crashes when you try to do it anyway.

Thanks, that's what I thought. I just find it tedious and frustrating mounting smb shares :(  -

regards

---

### Post by SigmundFreud on 2007-03-04
> **GuiGuy said:**
> Thanks, that's what I thought. I just find it tedious and frustrating mounting smb shares :(  -
regards
I completely agree. Also, I think a workaround where Amarok just downloads the file to a temporary folder and plays it from there would be a big help. But there was no inclination to implement that (it had to do with KDE4, apparently).

---

