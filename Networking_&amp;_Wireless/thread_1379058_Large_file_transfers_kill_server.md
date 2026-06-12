---
title: "Large file transfers kill server"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by RifterUT on 2010-01-12
So i have a home network setup with a server running Mint 8 64bit(ubuntu 9.10 based with more stuff preinstalled basically for those who dont know what mint is, uses same repos) I chose this OS because im planning on using this as a HTPC later and mint has all the multimedia codecs preinstalled so it would be easy to use for media playback. 
 
The server is running 3 1.5TB drives in RAID 5 with the linux software raid. Has a 500GB boot/OS drive. This is not a problem the array is fine and disks are healthy. I mounted the array to a folder and am sharing the folder with samba for the windows PC's on the network and NFS for the linux clients, for some reason i could not use just samba as the linux clients refused to see the share even though the windows clients could no problem. 
 
Anyways it all works fine till i try and transfer 50GB or more at a time. If i try and put a folder with 50GB or more data in it(various files 5MB to 3GB in size) onto the server both the client computer and server both crash. The client screen will turn really dark and you will not be able to use the mouse or any keyboard commands, forces a hard reset. The server will just lock up on the desktop, also doesnt respond to mouse or keyboard and requires a hard reset. 
 
I could transfer the files in small batches im just curious if there is anything i can do to fix this. 
 
Also should mention that i download torrents directly to the shared folder from any client PC/OS and can download a 50GB torrent no problem, the problem is only with network file tranferes.

---

### Post by RifterUT on 2010-01-12
Forgot to add, do you think its a nautilus problem? as it does not crash the server or client if i tranfer large groups of files from windows? how do i get rid of nautilus and whats a good file viewer program for gnome?

---

### Post by florenceit on 2010-06-29
Hi
I am wondering if you had any luck. I am having a similar problem with Ubunu 10.4 LTS. 

Mine starts working again after 2 minutes , but i can not copy large files. 

I also noted that it starts working again all by itself after about 1-2 minutes, but during the time the samba shares aren;t the only thing that stop working, its ALL networking:L web and ssh fail too. 

Matt:guitar:

---

