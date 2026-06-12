---
title: "Xubuntu File Server and Mac Behind NAT"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by hbost on 2009-08-17
Here is my dilemma:  I have two Macs in my house as my primary computers and use an Xubuntu Server running SMB shares as a file server for pictures, music, etc.  

Within my network (i.e. behind the router), I can access the Macs remotely from the Xubuntu box and I can access remote desktop, ftp, etc. back and forth between all of the boxes WHILE I AM BEHIND my router (i.e. using local fixed IP addresses).

I have finally gotten the courage to access my Xubuntu File Server over the internet using Dyndns.org.  I have figured out how to open an SSH tunnel and use both TightVNC and SFTP for remote desktop and file transfers with the Xubuntu Server only.  No problems...yet.  

I would like to be able to access the Macs remotely as well.  However, the only way I can get access to the Xubuntu server through SSH is to forward Port 22 to the Xubuntu Server.  If I do this, I cannot access the Macs as Xubuntu hijacks the port.

Clearly, this is either a port forwarding issue or a Mac sharing issue or both.  I have tried forwarding port 548 (AFP), 3283 (Remote Desktop), 5900 (VNC), etc.  I also have tried forwarding an "open" port above the 1200 range and to no avail.

Any help appreciated.  I am actually surprised I have gotten this far as I started the process from scratch (no linux background) about three months ago with an old Dell and two hard drives...  

Thanks.

H

---

### Post by superprash2003 on 2009-08-17
you can tell the mac ssh server to listen to another port instead of port 22

---

### Post by hbost on 2009-08-17
Thanks SuperP.  I think this is the heart of the problem -- a Mac issue instead of a port forwarding issue.

Fairly new to Mac -- not sure how to configure Mac SSH server.  Is there a utility?  Sorry for such a noob question.  

Much appreciated.

H

---

### Post by superprash2003 on 2009-08-18
check this out [http://www.freemacblog.com/mac-server-series-enabling-ssh-on-your-mac-server/](http://www.freemacblog.com/mac-server-series-enabling-ssh-on-your-mac-server/)

---

### Post by hbost on 2009-08-19
Thanks again, SuperP.  Will check out the tutorial video.  Great blog as well!

H

---

### Post by hbost on 2009-08-19
SuperP,

Checked out the video and it gets me halfway there.

What I am trying to do is log in from my work PC to my home Mac.  The issue is threefold:

1) I have both a Mac and an Ubuntu Server running behind a Linksys router with NAT/Port Forwarding capability.

2) I can forward port 22 (SSH port) on the router to the Mac OR the Xubuntu Server.  However, I can't figure out how to do both.  I think the issue is modifying the sshd_config script on both servers to listen to a different port, but I am tentative to modify the config on the Xubuntu server and have no idea where to even FIND the right script on the Mac.

3) I am also worried that I am leaving Port 22 open for all to see.  I need to figure out how to do key encryption, but not there yet.

Thanks again for the great start.

H

---

### Post by superprash2003 on 2009-08-19
well you have to make one server to listen on a different port , whichever you wish, the files to modify would be the same..
dont have to wrry about leaving the port open since it would be password protected

---

