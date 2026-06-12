---
title: "Networking Between Linux -&gt; OSX, XP and Solaris"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by timZZ on 2009-04-21
Hi Everyone,

Is the best setup to handle this.

OSX -> NFS -> Ubuntu Server Shares
Solaris -> NFS -> Ubuntu Server Shares
XP -> SMB -> Ubuntu Server Shares
Ubuntu Desktop -> NFS -> Ubuntu Server Shares

The shares are the same across ALL operating systems.

I have been told by some trusted individuals that Samba is more stable and if I could get away from it I should be using Samba for most of my connections.

Just wondering how true that is?

Also told that NFS is a far faster protocol.  Hence the intermixing of protocols.

---

### Post by puppywhacker on 2009-04-21
I'd stick to either samba shares or NFS 

A windows client is apparently part of Microsoft SFU Services for Unix.

* You don't have the complexity of setting up and maintaining two filesharing technologies.
* Your file permissions will be dealt with by one system
* File locking issues are contained better.

The transferspeed is related to your wirespeed. NFS is not significantly faster and Samba is not more stable. It always depends on your specific installation and configuration. I find NFS simpler in setup and Samba more complete. Samba has a windows style network sharing, NFS a more old school UNIX style sharing.

I'd pick samba, but the choice is very personal

---

### Post by timZZ on 2009-04-22
Thank you for your feedback it's appreciated.

---

