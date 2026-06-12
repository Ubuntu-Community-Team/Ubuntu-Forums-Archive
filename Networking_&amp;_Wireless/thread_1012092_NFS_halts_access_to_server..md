---
title: "NFS halts access to server."
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by ThaddeusW on 2008-12-15
Ok I have a big problem with my not so little Ubuntu 8.04 server. I was creating a backup of my laptop using NFS to my ubuntu server. I was also watching a movie that was on the same server using SAMBA played on my windows system. Now the video was playing fine until I started the backup and all access to the server was cut off save for ssh. The video froze and Apache which hosts my torrentflux server as well as test websites refused to respond and all SAMBA shares were inaccessible. 

What happened? The server always works fine but its like NFS hogs every last network resource. Thing is the server isn't a little pc. Its a 4U rack mount case with a dual 2.4GHz Xeons and 4GB of ram I got second hand. The board features dual on board Intel PCIX gigabit adapters (only using one though) so bandwidth, memory and CPU shouldn't be an issue here. 

The backup speed was about 11-12MB/sec and SAMBA is just as slow when copying to/from our desktops with fast SATA disks. I thought SAMBA was just slow but now even NFS is just as slow. Funny though, as HTTP copying is also about 5-6MB/sec. Its like the system cant cope with a gigabit network and NFS. I am running the NFS kernel-server and I have attempted to tweak the SAMBA config file with tcp_nodelay along with others but speeds still wont top ~12MB/sec. I have a 4 disk raid 5 using mdadm and copying to another SATA disk I see 50MB sec so disk speed is no problem either.    

This is frustrating as before I was using Linux I was using the Windows 2k server install that came on the server and it ran very fast with SMB network copies. I could easily get 25-30MB/sec over the network shares and multiple machines accessing it was no problem. And I am NOT going back to Windows 2k server. Any ideas?

---

