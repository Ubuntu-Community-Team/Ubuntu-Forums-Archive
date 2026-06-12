---
title: "Can't get Lucid Lynx to see Snow Leopard"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by FatLabs on 2010-10-11
I'm unable to get my Ubuntu 10.04LTS to see my Mac 10.6.4 machine.

I've got Samba and AFP enabled under the Mac file sharing preferences.

Attempt1: From Ubuntu, I can see my Mac under Network>Places, but I'm unable to mount the location.

Attempt2: In Ubuntu, I went to Places>Connect to Server and entered the following:
Service: Windows Share
Server: [name of my mac]
Share: [name of my shared folder]
Folder:
User Name: [username]
Domain Name: WORKGROUP

With this entered, I was able to get as far as being prompted for my password, but was still unable to connect.

Attempt3: I followed the same steps above, but left Domain Name blank.  Still nothing.


Are there any docs out there for the correct steps?  I can only find posts on getting Mac to see Ubuntu, but not the other way around.

---

### Post by FatLabs on 2010-11-23
Just trying to see if there's a solution out there for this.  No responses so far.


I have determined that Ubuntu has no problem seeing the FAT32 drive with a folder set to read/write for everyone.  But --- I really want Ubuntu to be able to see my Mac formatted drive.  There is no issue with other Macs seeing the drive --- only Ubuntu Karmic Koala & Ubuntu Lucid Lynx.

Any help out there to diagnose this problem?

---

