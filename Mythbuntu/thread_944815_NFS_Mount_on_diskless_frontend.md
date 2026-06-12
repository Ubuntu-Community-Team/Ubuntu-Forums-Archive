---
title: "NFS Mount on diskless frontend"
date: 2008-10-11
forum: Mythbuntu
---

### Post by gazza7 on 2008-10-11
Hi

I've got a diskless frontend working through pxe boot.
Everything works ok, except I cannot play my music collection which is located on the backend server. I have exported the directory, through /etc/exports . I have tested it by mounting it on the backend server with no problems.  But when I try to mount it on the diskless frontend, it does'nt mount. I get no errors, but the music is not mounted. This is the command I use on the  diskles frontend
sudo mount server://media/share/music /media/share/music

Any help will be appreciated

---

### Post by anonymousdog on 2008-10-12
Does that directory exist on the diskless client (i.e., on the compressed image or diskless cache)?  It must exist prior to the mount command.

---

### Post by gazza7 on 2008-10-13
Hi

Yes the directory exist on the diskless client.

---

### Post by Archmage on 2008-10-14
Is the IP-Adresse of the diskless frontend allowed to mount the folder? I think via default it is limited to 127.0.0.1.

---

