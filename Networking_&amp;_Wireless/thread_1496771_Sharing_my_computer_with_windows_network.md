---
title: "Sharing my computer with windows network"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by mister_lister on 2010-05-29
I have just installed Ubuntu 10.4 LTS and would like to share this computer on my windows network. I understand that Samba is the way to go, but how do I configure linux with Samba so I can share files and printers? I am able to see my windows computers (vista and xp) but I am not able to see the linux computer with those machines plus I would like to change the network name of the linux machine if possible.  Please any help and information will be much appreciated. Eventually I would like to server a printer from this linux machine to the other windows machines.

---

### Post by ixifx on 2010-05-29
smegging hell... I'm having the same problems

I went to set up shares the same way I did on 9.10, through the Shared Folders app under System \ Administration.

when I opened the app I was told I needed to install the packages to enable sharing, so I did (a totally painless experience).  but when I add a shared folder, I do not have the option to share it as SMB / Samba. I checked in Synaptic and Samba is installed.

---

### Post by mister_lister on 2010-05-29
OK, I figured out to share files with the linux computer to windows computers, I can read and write both ways... the outstanding issue is the printer I have connected to my linux computer, I would like to share it with other windows computers so they can print to it. Any help will be appreciated! Thanks in advance.

---

### Post by ixifx on 2010-05-29
Mr. Lister,

if you could enlighten me as to how you got the network up and running, please.

---

### Post by ronald.williamson on 2010-05-30
Likewise, I am having the same issue. Followed the instructions to install both sharing software but when attempting to share a folder there is no Windows SMB choice available. New install of 10.04 is the starting point - completely wiped the disk before install because of lost password.

I can see the folder on my Win XP and Win 2k boxes but when trying to drag file into the folder get a permission violation. This is essential to get up and running within 48 hours since the Linux box is to be used as a file sharing source for a major sporting event. Prior version was Hardy Heron and it worked well so perhaps I should revert back?

---

### Post by mister_lister on 2010-05-30
Essentially, to solve the file share issue, I simply shared a folder in my home directory (the "Public" folder) by right clicking on the folder and selecting "share". I was then given a prompt that I would need to install some software, I gave permission and when it was done I went back and shared the folder (didn't take the first time). After which I was visible to windows computers and they were visible to me. 

Still wondering about the printer share issue if anyone has ideas.

---

### Post by sgosnell on 2010-05-30
For the printer, System/Administration/Printing, select the printer and make sure it is set as shared.  

Samba works for file sharing, but I prefer NFS.  There are a number of threads and how-tos for this.  If you're already happy with the way samba sharing works, you don't need to bother with NFS, but it's my preferred method.

---

