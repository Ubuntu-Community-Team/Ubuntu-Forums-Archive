---
title: "Best multiplatform file transfer protocol"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by fela on 2009-09-02
What is the best multiplatform file transfer protocol? I'm wanting to push files to and from an Ubuntu Linux server using Linux, Windows XP, Windows Vista and Mac OSX clients (my house is multiplatform :P).

I've looked at Samba, which seems to me to be the FAT16 of file transfer protocols, if you see what I mean - compatible with everything but not particularly good. Also I don't know what its security is like, and I prefer it to be compatible with UNIX/Linux permissions. Right now I'm running a samba server on its home folder as a stop-gap solution but I'd love to use something more UNIX-like.

I'm also running an NFS server on its home folder, but AFAIK it's not compatible with windows. I'm only using Linux clients to connect to the NFS server, I haven't tried yet with OSX (but that has to be compatible surely, as it's UNIX?).

Of course there's also SFTP, the secure implementation of FTP (with SSH right?). It doesn't seem particularly fast in comparison to NFS and on the windows and mac clients it seems like I have to install a separate FTP client such as Filezilla, which doesn't really float my boat (I prefer it to be completely integrated into the OS).

So the question is, is there any blindingly obvious and brilliant multiplatform all-OS integrated protocol that I should be using?

Thanks

PS. Post on the poll which one(s) of these protocols you like (multi-choice)!

---

