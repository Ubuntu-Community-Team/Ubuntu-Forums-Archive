---
title: "networking question"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by kfitzenreiter on 2009-10-10
What I'm trying to accomplish is to give all my windows machines access to the fourth partition on my ubuntu box.
 
First I created the directory /home/kurt/Desktop/mycomputer/sda4 as a regular user.
 
Second I "sudo apt-get install samba".
 
Then I edited /etc/fstab and entered a line reading...
 
"/dev/sda4 /home/kurt/Desktop/mycomputer/sda4 vfat user,auto,fmask=0111,dmask=0000 0 0" 
 
doing so as root.
 
Then I right click the sda4 folder to set up sharing, but this requests an edit to 
the file /etc/samba/smb.conf. First of all, I forgot to mention setting the "workgroup=Mshome". But also, I add "usershare owner only = False"
 
The problem comes when I try to go in from windows xp. It gets to the folder okay but then asks for a user name and a password. I enter the names from the ubuntu box but it rejects it. I even tried "sudo smbpasswd -a username" but this did not solve the problem.
 
The goal here is to be able to get to the folder but to also require a user name and password to do so.

Any thoughts???

---

### Post by sandyd on 2009-10-10
make your ubuntu username and windows username the same.
then try again.

---

### Post by gletob on 2009-10-10
I would highly reccomend only placing mount points in the designated /media and /mnt folders, for starters.

---

### Post by rb0171610 on 2009-10-11
> **gletob said:**
> I would highly reccomend only placing mount points in the designated /media and /mnt folders, for starters.
I am the only user on a secure home network. 
I have been mounting my samba shares, windows drives, and NFS shares into a subdirectory in my /home directory for years and never had  a problem.  I don't think it makes any difference.  It is your home folder, do with it as you wish.

 /mnt and /media can be used as well.  This is where some distributions automount media though.

---

### Post by Iowan on 2009-10-11
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a good How-To on mounting CIFS shares. I've seen some threads recommending installing smbfs as well (maybe that was a version or two ago...).
I presume the username/password you use is the one under whose /home directory the share is mounted (kurt)?

---

### Post by rb0171610 on 2009-10-11
Are you still having problems?


Rob

---

### Post by kfitzenreiter on 2009-10-11
> **carlee said:**
> make your ubuntu username and windows username the same.
then try again.

Thanks for your reply, Carlee.

I tried that, but after the fact and it was giving me fits.  I toyed around with reinstalling ubuntu and starting from that point with that name.

Another problem with that scheme though is the fact that I have different log on names on different windows machines, so no matter which one I pick for ubuntu, it won't be the same on all of them.

It works now but only with "Guest access (for people without a user account) " checked off in the "file manager" folder sharing popup box.  I guess I may have to settle for this setup, although I had hoped I could configure it to require the username and password for any machine.

---

### Post by Iowan on 2009-10-12
There is (or was) a Samba **username map=** option to map Windows users to Linux users. I'm drawing a blank on it's details right now, though...

---

### Post by kfitzenreiter on 2009-10-14
Hi rb and thanks for your reply.

Everything is working in the sense that I have the shared folders properties set up with guest access.  I was hoping to configure a username/password scenario from any windows machine, but I think it might be easier to reinstall windows than to try to undo everything I did on ubuntu, if that makes any sense.

Besides I just got sidetracked by freenas OS as Networked attached storage for an old pentium III box that just doesn't have the cajones to run xp or ubuntu with any pep.  It is working with freenas however and talks to both my windows and my ubuntu boxes.

The quest for PC nirvanna continues...

---

