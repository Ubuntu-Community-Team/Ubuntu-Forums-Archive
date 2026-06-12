---
title: "Create NFS share from smb mount"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by snowglyder on 2009-09-28
Is it possible to mount a Windows smb share on a Ubuntu desktop, then (re)share the smb mount or a sym link for nfs clients to connect to?

Here's what's happening: We're using a server with ubuntu as an imaging server, using FOG. We're running out of space on the server, with no open slots for expansion, so I wanted to use our clustered Windows 2003 storage server to store the images. I'd like to keep the paths the same (//ubuntuserver/images) since the path is used throughout FOG. Is it possible to mount the Windows share (/mnt/images), create a sym link (/images) to /mnt/images, and create an nfs share from the sym link? I've tried, but haven't been able to get the sym link to share. I get an error "does not support nfs export" when I try this. 

Any ideas or different ways I can get the same results?

---

### Post by inobe on 2009-09-28
the wiki explains how to add a storage node.

10.5

and 10.5.2

here

[http://www.fogproject.org/wiki/index.php?title=FOGUserGuide&Itemid=51](http://www.fogproject.org/wiki/index.php?title=FOGUserGuide&Itemid=51)

---

### Post by snowglyder on 2009-09-29
I do have different storage nodes setup for different sites. I'd really like to use the space on a current Windows 2003 storage cluster. I've created an NFS share from the Windows server, but I still couldn't re-share, or sub-share, the mounted folder. Or even create an NFS share from a folder within the mounted NFS share.

---

