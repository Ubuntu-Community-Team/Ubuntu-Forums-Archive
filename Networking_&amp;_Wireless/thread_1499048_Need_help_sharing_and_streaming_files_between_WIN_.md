---
title: "Need help sharing and streaming files between WIN 7 and Ubuntu"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by Casper34 on 2010-06-01
I am having issues connecting my laptop (Ubuntu 10.04) to my PC (Win7). I have tried to follow the Samba peer-to peer tut, but when I start Samba, it cant be found. I would prefer to have a GUI version over Terminal, but i can do Terminal if need be.

I can get online with no problems. When I go Places, Network, my PC is listed. I click on it and i get 1 of 2 errors.

Error 1: On the PC if I have "file and printer sharing" turned ON I get "Password required Blaa Blaa Blaa". I never setup a password for sharing. If i click continue, it pops back up again.

Error 2: On the PC if I have "file and printer sharing" turnned OFF i get "opening PC" then "Unable to mount location, Failed to retrieve share list from server".


Now if I go into Smb4k, if i click on "workgroup" the PC is listed. I click in it with "file and printer shareing" OFF i get "the list of files cannot be retreived" Details: Invalid command: net rap share list.

If I turn ON "file and printer sharing" it quaries it, done. but i still cannot connect to any files on my PC.

Also, I have another PC that has WIN XP Pro on it and i can access the shared files there with no issues. All my music and videos are on my Win7 PC and thats what I need to connect to.

From what I am seeing, re-reading what i just typed out, that it seems to be a Win7 setting problem. But i dont know where. Can someone please help me?

---

### Post by arvevans on 2010-06-01
There seems to be an assumption that the solution is with Ubuntu, not that there may be a problem associated with Windows-7.  The statement that this works with Microsoft-XP but does not work with Windows-7 seems to indicate the problem being in Windows-7.  Maybe this question needs to be posted on a Windows-7 support group.  Others have probably already hit the same problem, and may already have an answer available.

Now, having said that (I feel better now!), there are several ways to work around the problem.  As you noted, one could use 'ftp' as a file transfer method.  'Telnet' can also be used for remote operation of a Linux host and for file transfer.  The various versions of 'vnc" provide both generic and secure methods for remote operation of Linux systems, and include ability to cut and paste files between the client and host systems.  While 'nfs' is sometimes difficult to get working by non-UNIX/Linux trained persons, it is the original and fastest Samba-like method for file sharing and even remote-booting between client and host computers.

You may still want to work on making Windows-7 compatible with Samba and Linux, but until you get that working, there are several viable alternatives.

---

### Post by Casper34 on 2010-06-01
Ok, but i dont just want to transfer files from the PC to the Laptop (Ubuntu). I have all my movies on my PC and it is way easier to hook my LT up to my Tv to watch then then my PC. I dont want to have to transfer the files from the PC to my LT to watch them. Can Samba do that? If not, is there something out there that can? 

I have had Ubuntu on my LT for 2 days and this is my first Linux System.

---

