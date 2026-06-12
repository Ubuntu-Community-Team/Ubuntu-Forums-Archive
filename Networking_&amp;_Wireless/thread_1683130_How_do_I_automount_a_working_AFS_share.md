---
title: "How do I automount a working AFS share?"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by caressati on 2011-02-07
(System: Ubuntu 10.10 on HP Compaq 6720s laptop)

I'm trying to access my iMac OSX shares through a recent laptop Ubuntu install. OSX is set up to allow AFP sharing of selected folders, and after installing Netatalk, finding the folders on the network and mounting them in Ubuntu works just fine.

However, I would like to automount one of the folders whenever I start the computer. Is there an easy way to do this?

I've automounted a Time Capsule in /etc/fstab using:

//ip/folder /media/folder cifs password=pw,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

But I can't seem to repeat the success with the OSX folder. I've tried various versions in the terminal but I can't get it to work.

Any help would be greatly appreciated. Especially if I can do it in a gui. :)

Thanks!

---

### Post by caressati on 2011-02-07
Hmm. I've managed to mount it in the terminal using smb now:

sudo mount.cifs //ip/folder /media/folder -o username=user,pass=pw

But I'm getting permission errors in Nautilus. I'm confused.

Edit: I've also managed to mount it using afpfs-ng (sudo mount_aftp url folder), but I still get permission errors. Evidently this is due to settings on my OSX computer, so I don't really know what more to set. I'll mark this thread as solved, because it is now an OSX error and not an Ubuntu one. Thanks for reading.

---

### Post by cleopete on 2011-03-08
I just finished dealing with some annoying permission errors as well.  After hosing my Ubuntu install by modding it's permissions, I reinstalled and ran "sudo chmod 777 ~/StupidProprietaryMacSystemFolder"  in the OSX terminal.  That did the trick, you may need to go into system info and give "group" read/write access.  I just Googled that to see if I typed that right and it appears a lot of people say to add the -R switch after "chmod".  I don't think I did that but I don't have a way to check my work at the moment.

Now I have to figure out how to automount folders from my Mac partition...

---

