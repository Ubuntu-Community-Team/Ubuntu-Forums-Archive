---
title: "Network/File Sharing W7 and Ubuntu"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by designingpatrick on 2012-10-20
I am in need of a workflow solution.

I am creating motion graphics in Ubuntu 11.04 (using Luz Studio) and compositing in After Effects/Premiere in Windows 7.

Currently, my workflow involves rendering frames in Ubuntu, then transferring them to an external drive, then downloading to my W7 desktop. This is time consuming, and frustrating, as I believe that there is a better way.

I have looked around the net to find a way to share files using a LAN/Home Network, but have yet to find a solution.

I am an animator, and I don't have the background to fix the problem myself. I am willing to go through any steps needed to get this working, but don't know where to start and am unsure if there is even a way to get the results I need.

Any help on this?

---

### Post by Merrattic on 2012-10-20
Two different PC's -  yes?

Choices:

1. Set up your ubuntu PC as a samba server, then your W7 PC will be able to see the files on the network
2. Add a third PC as a server, running samba, file sharing as above

If dual booting, on the same PC, simply create a "DATA" partition as ntfs which ubuntu can see and is natively available to W7

or find a compositing solution on ubuntu....(sorry don't have an answer for this bit :()

---

### Post by designingpatrick on 2012-10-20
2 pc's, yes.

I will need to investigate the Samba server option- I'm hoping that this isn't intrusive to my current setup, and that there is a way to maintain already existing network configurations (for windows to windows communication).

Unfortunately, I don't know of any, and would be leery of Ubuntu compositing apps ;)

Thanks for the options!

---

### Post by ahallubuntu on 2012-10-20
Sharing in Ubuntu no longer requires setting up a "samba server" in the formal sense; rather, you can share simply by right-clicking on any folder you wish to share and choose the "sharing and security" option to share that folder.  The first time, you'll probably be asked to install some stuff for sharing.  After that, it's easy. 

(You are basically using Samba to share this way, but there is no need to create a configuration file or anything, it's done for you automatically.)

Try it!  I've shared in 11.04 and it works pretty easily.

You can try guest access, but requiring a password is of course more secure.   You can use your Ubuntu login/password for that.

---

### Post by designingpatrick on 2012-10-20
Dude... you are totally righteous. This ACTUALLY worked. You have no idea just how skeptical I was as I followed these few and suspiciously simple steps towards streamlined, cross-platform creativity.

Thank You

---

