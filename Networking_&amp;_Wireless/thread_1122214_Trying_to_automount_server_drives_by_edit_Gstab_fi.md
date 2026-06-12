---
title: "Trying to automount server drives by edit Gstab file - not working"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by daaussie on 2009-04-10
Hi,

Trying to automount, but the command does not work.
What am I doing wrong or what haven't I done?:

//192.168.1.3/public/<<SERVER DRIVE NAME>> /home/<<workstation name>>/SERVER DRIVE NAME smbfs

I have done lots of reading, but can't find an answer.

I tried putting in sudo mount -a underneath and creating the SERVER DRIVE NAME in the "home folder" on the workstation.

---

### Post by daaussie on 2009-04-10
Ok, I figured it out:
You need to do 2 other things:
1. Go to terminal type sudo apt-get install smbfs
2. Create the folders that are specified in the home folder (i.e. go to home folder and create SERVER DRIVE NAME
Yahoo!

---

