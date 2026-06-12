---
title: "how to acces a network folder in a software"
date: 2013-08-19
forum: Multimedia Software
---

### Post by zoula on 2013-08-19
Hi,
I'm new to linux and I would like to go on with linux  but I'm facing a big stop.  I have a big discotheque on a windows PC  that I don't intend to change location.  I could see all my files in the  file browser of Ubuntu,  My problem is that in whatever program I use I  can't get my files from the software.  The file browser in all the  software don't show network.  


So I can't add a file from  the software and I can not tell the soft where is my Library,  even if  the network file is mount.  Why is the network file don't show in the  file explorer of software???  


Thank you

---

### Post by Mark Phelps on 2013-08-21
> My problem is that in whatever program I use I can't get my files from the software

Since you can see the files in the browser, the problem is that the programs you are using don't allow you to browse networked filesystems.

If you tell us what programs, we may be able to suggest alternative ones.

---

### Post by zoula on 2013-08-21
I tried almost every music software that you can think of...  But to simplify this post, let's concentrate with Gmusicbrowser.  When I try to search for a location for my library. In the preference menu when the little file browser open I can not see my network.  The same thing happen when I try to open a file from the "file open" menu.  
I use Nautilus for file browsing and I have absolutely no difficulty do see my network, but from a software it seems impossible???

Thank's

---

### Post by steeldriver on 2013-08-21
What version / flavor of Ubuntu? If the network browsing is handled by gvfs, you may be able to access your remote share programatically via the gvfs usermount - in Ubuntu 12.04 that should be at ~/.gvfs (i.e. /home/username/.gvfs) e.g.

```

$ ls ~/.gvfs
users on winbox
$ 
$ ls ~/.gvfs/users\ on\ winbox/ 
Default
desktop.ini
steeldriver

```

although I believe it has moved in newer releases to somewhere like /run/user/XXXX - if you're not sure you can use the 'mount' command e.g.

```

$ mount | grep gvfs 
gvfs-fuse-daemon on **/home/steeldriver/.gvfs** type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=steeldriver)

```

---

### Post by texaswriter on 2013-08-23
Did this resolve the issue?

---

