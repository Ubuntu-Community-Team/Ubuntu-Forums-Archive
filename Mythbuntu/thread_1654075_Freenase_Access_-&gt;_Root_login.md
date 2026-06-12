---
title: "Freenase Access -&gt; Root login ??"
date: 2010-12-27
forum: Mythbuntu
---

### Post by moe411 on 2010-12-27
I'm a new user and not familiar with Ubuntu. I installed Mythbuntu and played a DVD on my Flat Screen TV and it worked fine. 

Now I want to access my music and videos which are on a freenas box. I created a directory to use as a mount point but when I try to use the mount command I get an error 

-> mount: only root can do that

I am using the terminal window under applications menu. I tried logging out but it doesn't work.

How do you log in as root on a mythbuntu box ? Also once I these drives are mounted how could I mount them automatically ?

Thank's for your help,

---

### Post by ian dobson on 2010-12-28
Hi,

To run a command as root use su. So to mount a drive use
sudo mount MountPoint DEV

To always mount a drive you need to edit /etc/fstab as root:-
sudo nano /etc/fstab 

note nano needs to be installed, to install nano type
sudo apt-get install nano

To run all the above commands you just need to start a terminal, there's a menu option for that. 

Regards
Ian Dobson

---

### Post by moe411 on 2010-12-29
Hello Ian, thank's for the help, I can finally mount my drives now. Not sure about editing /etc/fstab, do I just copy the same command line in this file and it will run it on boot or do I need to write something else ?

Thank's again,

---

### Post by newlinux on 2010-12-29
> **moe411 said:**
> Hello Ian, thank's for the help, I can finally mount my drives now. Not sure about editing /etc/fstab, do I just copy the same command line in this file and it will run it on boot or do I need to write something else ?

Thank's again,

The syntax for /etc/fstab is different from the commandline mount command.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Gives good information as does 

man fstab

---

