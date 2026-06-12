---
title: "Don't know what exactly kind of network I need for this :("
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by CrazyDesi on 2008-12-18
Here is my dilemma.  I have a bunch of files that I need stored and accessible from anywhere.  I would like to be able to work with these files kind of how Dropbox works.  A folder on my computer that I can connect to.  I don't know what kind of network I need for this.  If I wish to work on the folders locally when I travel, do I need OpenVPN set up or is something simpler available.  I am confused on the difference between OpenVPN, Samba, and NFS.

---

### Post by Sam Lars on 2008-12-18
Samba is the Windows file sharing service.  If you want to use Windows to see the files on your Linux machine as if it were sharing them as a Windows machine, you want Samba.
NFS is better suited for using Linux to see files on another Linux machine, but you could probably get an NFS client for Windows.
If you run Linux, you can mount either one to a local directory, so when you edit files in /whatever/whatever, you're changing them on the server.
If you leave home, you would have to have your home computer accessible from the outside in order for this to work.  Dropbox would work well in that situation.

---

### Post by CrazyDesi on 2008-12-18
Is there a way to mount a whole disk like Dropbox?

---

### Post by Sam Lars on 2008-12-18
What do you mean by that?

---

### Post by CrazyDesi on 2008-12-18
Well when I am lets say at my schools network and I wish to access the files on my home network(for instance videos or something large).  Can I just play the videos or files off of the network or do I have to FTP and copy them locally first?

---

### Post by Sam Lars on 2008-12-18
Dropbox will automatically synchronize your local copy with the online copy, but it will take a while for videos.
Mounting an NFS or Samba share would look like it's local, but it would in actuality be accessing the files over the network, so you should probably copy them locally if you don't have a fast connection.

---

