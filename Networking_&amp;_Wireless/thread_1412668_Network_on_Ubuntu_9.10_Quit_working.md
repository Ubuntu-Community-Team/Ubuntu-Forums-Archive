---
title: "Network on Ubuntu 9.10 Quit working"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by lineback on 2010-02-21
I was sharing files between my desktop and laptop with no problems for over a year.  They are both running 9.10.  I noticed that several people were using my wifi so I put a wpa encryption on my router.  After that all of my shares in the network disappeared.  I removed the encryption but the shared did not come back.  Any help would be much appreciated.

---

### Post by The Toxic Mite on 2010-02-21
Hey! Did you type in your WPA key on the other computer? That might help. :-)

---

### Post by lineback on 2010-02-21
Maybe I used the wrong terminology.  The network works; the network shares are what is gone.

---

### Post by lineback on 2010-02-21
Is there any one that can help me with this?  Or possibly point me to another thread that will help me?  I have been trying to figure this out for over a week.
Here is some more info.
My DAAP share for music still works.
My printer share still works.
However, there is nothing when I go to network in nautilus.  
Previously, when I clicked on network there would be my desktop, my laptop and a windows network folder.  Now there is only the windows network folder.  When I click on that it returns an error saying it could not mount the location.

---

### Post by northd_tech on 2010-02-21
What OS'es are the desktop and the laptop running?  Are they dual boot with Linux and Windows?  Wired or wireless connections?  Are you sure that all the network connections are working (via ubuntu terminal commands** ifconfig, iwconfig, sudo iwlist scan, ping**, web browsing, etc.)?

If you are using Windows Networking to share the folders/printers/media whatever, you will need to read up on Samba for ubuntu.

Here is a quick overview:

[http://learn.clemsonlinux.org/wiki/Samba_client](http://learn.clemsonlinux.org/wiki/Samba_client)

Here is the main page that has tons of information:

[http://www.samba.org/](http://www.samba.org/)

A search here at this forum for samba, wep, wpa, etc. should bring up many threads.

If you just want to use Linux sharing, you've got many ways to do that: mirroring, sftp, setting one computer up as a file server, etc.  Printers vary a lot (and that's mostly how/why I've shared resources in both Windows and Linux).

---

