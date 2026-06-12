---
title: "which filesharing protocol?"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by mistafeesh on 2010-11-30
Hi,

I have a small home/office network, which currently consists of a very old mac running osx10.4, a windoze 7 laptop and an ubuntu 10.04/windoze vista laptop, along with a homebrew setup on a wii which understands smb.

 I'm in the process of setting up an additional ubuntu PC which will, among other things act as a file and web server, mainly for web development and for sharing files, music and videos.

Up until now I've just run everything on SMB, and I will have to set samba up on the new server, but I would prefer to use a different protocol for the ubuntu and mac systems, as SMB doesn't recognise/create file permissions properly and it takes a while sometimes to notice new files in folders it's recently looked in.

any suggestions?

---

### Post by surfer on 2010-11-30
i have never tried it. but what about [WebDAV]("http://weblog.bignerdranch.com/?p=18")?

---

### Post by Boondoklife on 2010-11-30
If you really have your heart bent on moving, try nfs, I think it can work on all three with the right software.

---

