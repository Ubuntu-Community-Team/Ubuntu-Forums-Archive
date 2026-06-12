---
title: "Need help setting up network folders accessible by all users"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by tommyb on 2006-06-03
I have just installed Ubuntu server 6.06 as a file server on my network.  I have Samba installed, and can see the shared folders from all the machines on my network. (I am also a Linux newbie, and it took lots of RTFM to get this far...)

Where is the best place in the file system to make folders accessible to all users?  If I make it under a particular login name, I can access it from the Windows machine with the same username with full permissions, but if I access from another machine with another username, I can see files, but lack write permissions.  (I added the user in the terminal with "sudo sambapasswd -a username")

If I am missing something in the big picture, please answer in enough detail for  a Linux newbie to figure out.  I am trying to find a server solution that works for all my Windows network clients...

TIA,
tommyb

---

### Post by Jason_25 on 2006-06-03
I use security = share for anonymous samba access.  But if you have network shares that you also want private, you can't do it that way.

---

### Post by tommyb on 2006-06-03
OK, for those who don't know (and I didn't), the security=share that Jason_25 is referring to is in file system/etc/samba/samba.conf

You cannot edit this file without root privileges.  I opened a terminal and entered sudo gedit, then browsed for the file.  Does anyone know a better way?

the default is ; security=user   you need to remove the semicolon as well as change user to share.  This is working for now, but is not the answer.

This works by disabling security, doesn't it?  Can anyone give me a way that I can share with security=user?

Also, this begs the question of where in the directory structure is the best location for a shared data folder.  Also,  my data is a second hard drive.  I did figure out how to automount it, but am still unsure of the best mount point location for shared data as well.

tommyb

---

### Post by blackjack6.21.91 on 2006-06-04
I really don't understand?  What is it that you want to have on your network?  Who do you want to be able to write/read to your files?

I think that most people share their home folder and put their mount stuff in /mnt.  But there are no folders that are intrinsically better to share than others.

You can go to applications --> system tools --> run as a different user
and in the window that opens up
run: nautilus
user: root
If you dont see the "run as a different user" icon (and thats fine), right click where it says applications, click edit menus, go to system tools and check the run as a different user box.  Then everything should work out.  Hope I'm helpful.

-Myself

---

### Post by tommyb on 2006-06-04
I administer lots of Windows networks.  All are slightly different.  I am looking for an alternative to a Windows server.  The file server needs to have a central repository of files that all users can access, as well as folders for files belonging to each individual.  It would be best if each user had to log in to access them.

If I create a folder as root, and share it, then I need to assign permissions as root to read/write, correct?  After I do that, can I assign permissions to subfolders only to root, and one individual?

Thanks for the tip about the "run as different user"  My install did not even have "system tools".  I did not know I could edit the menus...  

tommyb

---

