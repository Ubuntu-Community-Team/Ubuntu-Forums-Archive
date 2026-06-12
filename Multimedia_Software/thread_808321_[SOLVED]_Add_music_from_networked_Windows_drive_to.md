---
title: "[SOLVED] Add music from networked Windows drive to Amarok"
date: 2008-05-26
forum: Multimedia Software
---

### Post by ACTPOHABT on 2008-05-26
I'm trying to add my music collection, which is located in Windows Vista shared folder (NTFS drive), to Amarok running in Ubuntu 8.04 Gnome. I can access that folder from Places-Network.... but I can't see it listed when pressing Add Media in Amarok.
Would really appreciate some help and thanks in advance!

---

### Post by ACTPOHABT on 2008-05-26
Anybody?

---

### Post by ACTPOHABT on 2008-05-26
bump

---

### Post by ACTPOHABT on 2008-05-30
any ideas?

---

### Post by Maratonda on 2008-05-31
That's what I did.
Linked the Music folder located in NTFS on my desktop.
Then added the linked folder.

---

### Post by ACTPOHABT on 2008-05-31
> **Maratonda said:**
> That's what I did.
Linked the Music folder located in NTFS on my desktop.
Then added the linked folder.
If I try to right click that folder and create a link to it, it gives the error "Symbolic links only supported for local files"?

---

### Post by ACTPOHABT on 2008-05-31
And when I try to do this: "sudo mount -t smbfs -o username=myusrname //192.168.1.101/d$/music /media/vista", it gives me this error: "mount error: can not change directory into mount target /media/vista".

---

### Post by Maratonda on 2008-05-31
Can you play the files individually? I mean, you browse to the ntfs music folder and open with some player? Just to make sure it's amarok's problem and not some kind of access problem.

---

### Post by ACTPOHABT on 2008-06-01
> **Maratonda said:**
> Can you play the files individually? I mean, you browse to the ntfs music folder and open with some player? Just to make sure it's amarok's problem and not some kind of access problem.

I can.
Anyway I switched to gmusicbrowser. Sees networked drive by default. I guess Amarok is not there yet. Solved. Closed.

---

