---
title: "Can't see server in places -&gt; network"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by ipage on 2009-12-01
Hi all,

This is my first post here, having recently converted from the dark side.  I've been using Ubuntu for a month or so on my work lappy, and decided to have a go at setting up a server for home (mainly as a file server / music server).  I thought I'd be brave and install the server edition (9.10), and despite some interesting times during install (I thought I'd make it extra difficult for myself by setting it up as RAID 1 at the same time) it seems to be working fine.

However, just after I finished installing, I'm fairly convinced that I could see my new server from my laptop in Places -> Network, but it's not there any more!  I'm sure it *was* there, because I remember thinking how cool it was that I could see it.  I can ping, SSH, and connect to it from Places -> Connect to Server, but I wanted it to just appear in my list of network machines.

Am I missing something?  Or was I just going mad when I saw it (it was very late / very early!)?  It's no really big deal, but if there's someone out there who can give a bit of an overview of Linux networking I'd be grateful.  I don't really want to bother with samba (I don't have any Windows machines that need to connect), and I know there's NFS (although I don't really know anything about it), but that's not installed as far as I can tell, so I'm not sure how I managed to see the machine.  Is there something else that's installed by default that would have allowed me to see it? I would have thought that I would be able to at least see the other machine, even if permissions stopped me accessing anything.  Or do do I still have my Windows hat on?  Or perhaps I am going mad after all...

Many thanks in advance for any help / advice!

---

### Post by ipage on 2009-12-02
OK, maybe that was a bit long winded.
 
What's the simplest thing I need to do so that my Ubuntu server is visible to my Ubuntu laptop in Places -> Network?
 
Thanks...

---

### Post by Iowan on 2009-12-02
See if it shows up in Places>Connect to Server. You *may* need to install Winbind and edit **/etc/nsswitch.conf** (per [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To).

---

### Post by ipage on 2009-12-07
Yes, if use connect to server, I can see it.  I suppose I was really wondering why the only thing I can see in Places -> Network is my samba share.  I would have thought that the server would be there, and that I could provide the credentials when I click on it.  Or do I need to set up NFS for that?

---

### Post by Iowan on 2009-12-07
Honestly, I haven't yet used NFS - even between Ubuntu machines. There are Windows machines on my network - so I leave everything in Samba.

---

### Post by ipage on 2009-12-08
OK, I might give it a try - there are enough posts out there on how to set it up.  It's more for curiosity now than anything else...

Thanks for your advice!

---

