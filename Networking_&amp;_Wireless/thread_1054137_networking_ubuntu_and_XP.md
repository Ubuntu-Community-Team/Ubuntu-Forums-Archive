---
title: "networking ubuntu and XP"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by RogerD on 2009-01-29
Hi

I want to be able to copy/share files and folders between my Ubuntu 8.04 desktop PC, called roger-deskop-new, and my new Samsung Nc10 notebook, running Windows XP, whose computer name is 'notebook'. Within Ubuntu I've made real progess - I can access shared folders on notebook and copy files from Ubuntu to Windows XP. What I can't do is go the other way, because I can't 'see' my Ubuntu PC from within XP. I don't know much about XP - haven't used it in anger for years - but I'm pretty sure that I need to:
start>My computer place>add a network place, but I get stuck when I'm asked to add the Internet or network address. I've tried the Browse button, hoping it would find roger-desktop-new, Ubuntu managed something like this, but no joy. Not a great deal of cop XP.

All help and advice much appreciated.

Roger D

---

### Post by flytripper on 2009-01-29
I'm not a great tidy network manager but you have to have a share on the ubuntu pc for the xp machine to see it. try starting with your public folder.. right click and share it and allow changes to be made... and if it isnt already, the ubuntu pc will install samba off the net so the shares will work.. hope this helps

---

### Post by jmore9 on 2009-01-29
It has been a long time since i tried to access a linux part from winxp.  Other than a server.  But I believe that you need to have a FAT32 or NTFS partition on the linux side for windows to work with.  I don't think it will work with EXT3 , etc partitions, without using a third party app.

Hope this helps

---

### Post by Coreigh on 2009-01-29
You have to have Samba server installed and you have to have the two computers in the same "WorkGroup" Windows usuall makes this 'MSHOME' by default but you can make it what ever you want as long as they match between XP and Ub.

Here is a basic how to:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by sedawk on 2009-01-29
Some people here seem to have problems accessing a share from
a Ubuntu machine from XP or Vista. (Samba software is used
to configure and run the share).

If you run into the same problem you can try to use the secure ssh protocol
for simple file transfer between the two machines (sftp). On Ubuntu
install openssh-server and on XP use either the "putty" stuff or
install Cygwin with ssh. I like to run an ssh daemon (sshd) on
XP with Cygwin so I have remote access if the desktop freezes and
I'm still able to login and shutdown the machine from command line!

---

