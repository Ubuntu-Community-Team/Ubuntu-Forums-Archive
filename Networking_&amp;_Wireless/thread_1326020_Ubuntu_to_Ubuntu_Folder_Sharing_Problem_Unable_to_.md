---
title: "Ubuntu to Ubuntu Folder Sharing Problem Unable to Mount Location"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by davidoloan on 2009-11-14
Hi,

I need a bit of help with "shared folder" problem. I am new to Ubuntu and love it.

I have installed 9.10 **server** on an old Dell I had and put it in the roofspace (its noisy and huge :sad:). I have connected it to our printer and have successfully made it our print server with 4 notebooks running Ubuntu 9.10 printing wirelessly. It was easy for a beginner :D I like Ubuntu; it was an uphill struggle at first, but as an "ordinary Joe" I can now get it to do most things I want and non of the computers in our house have crashed or infuriated me since I converted them starting in May.

Then I created a folder called "backups" in Documents on the server. I right clicked on it, entered sharing options and set it so that other people could write to it and anyone on our Network could access it.

In order to do this I had to install Sharing Service which was successful.

The problem is that although on the notebooks I can find the folder "backups" by going to places, then Network, then "server" (the name I chose for the Dell) then backups, when I try to open it I get the message** "Unable to mount location Failed to mount Windows Share"**.

I have been looking at this thread [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149) but its all Windows and my problem involves Ubuntu to Ubuntu sharing. Have I made some error by installing Samba? 

When I click on properties of the shared folder (Backups located on the Server) on the notebooks its Location is smb://server/

I would appreciate any help or pointing me in the right reading direction. (All computers on the network are Ubuntu)

Thank You, David

---

### Post by Iowan on 2009-11-14
The author of the thread you mentioned has a few links in his signature. For an all-Ubuntu network, NFS might be easier to use than Samba (although Samba can work...). He also has a couple of links for setting up FTP-server. 
If you intend to make the Samba server a more-or-less permanent connection, check [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To for mounting CIFS shares.

---

