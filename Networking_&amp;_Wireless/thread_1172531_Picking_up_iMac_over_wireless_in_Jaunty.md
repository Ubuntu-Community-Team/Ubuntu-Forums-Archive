---
title: "Picking up iMac over wireless in Jaunty"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by Ace1989 on 2009-05-28
Hey /uf/ - 

I have an iMac and an Acer Ubuntu laptop running Jaunty. How can I make it where my laptop will always pick up the iMac HDD and automount it so I can acces files and play music from that drive?

---

### Post by pytheas22 on 2009-05-28
There are lots of ways to do this.  [This page]("http://www.moixo.com/es/sharing-files-folders-from-ubuntu-to-mac-os-x"), which explains how to share files between Macs and Ubuntu using samba (Windows' network-sharing protocol), is a good place to start.  You can find other instructions if you google something like 'ubuntu share files with mac'.

If you want to mount the entire Mac hard disk on Ubuntu, NFS would probably be the easiest way to do that.  But samba might be a simpler approach if your end goal is really just to share media files, not necessarily 'mount' the drive over the network in the proper sense of the term.

---

### Post by Ace1989 on 2009-05-31
I managed to get OS X to pick up my Ubuntu laptop by installing Samba and opening up my home folder, but I can't seen to get any of that stuff working in Ubuntu that you have listed. It seems those instructions won't work for Jaunty.

---

