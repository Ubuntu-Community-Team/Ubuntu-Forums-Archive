---
title: "VLC under ubuntu"
date: 2016-07-26
forum: Multimedia Software
---

### Post by blumbly on 2016-07-26
Hi guys just recently started using ubuntu as I feel it's a better os. Now I know you've properly revised so many questions about VLC on ubuntu and I'm sorry I have another one to add to it.
Under windows if you wanted to watch a show/movie over my home network.All you needed to do was open VLC click on Media,Open file,network find the computer you wanted.Drive file is on then find file then click open and it would run.If there was more than one file and wanted to view them all then you could select them all,and it would play them in order.I have noticed on ubuntu that same process doesn't work.So I have to search the network and find the file and tell it to run on VLC. Which is a lot more involved in the search for the file I want.
Is there an easier way to do this process?
Thanks all.
Blumbly

---

### Post by T.J. on 2016-07-26
Windows file sharing requires that Linux use SMB protocol - aka Samba.  You will have to install it.  

sudo apt-get install samba
sudo systemctl enable samba

Then reboot.

However, Samba does NOT support Windows 7/8/10 Homegroups because Microsoft changed the networking.  You will have to setup manual file sharing for those machines.

---

