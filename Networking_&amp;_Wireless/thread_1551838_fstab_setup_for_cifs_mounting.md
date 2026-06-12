---
title: "fstab setup for cifs mounting"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by aasmith on 2010-08-12
Hopefully this'll be an easy one (but I wasn't able to find any other posts with the exact same problem).

I'm connecting to a large hard drive at work. I can mount perfectly fine. The following is the relevant line in my fstab file:

//XXX.XXX.XXX.XXX/data   /mnt/labdata   cifs   users,rw,exec,suid,dev,username=XXX,password=XXX,_netdev,fmask=777,dmask=777   0   0

The problem is that when I try to cd to the correct directory, I get a permission denied error.  I don't own the mount point, and there aren't general read/write permissions set.  But if I change to superuser, I can access it no problem.  I can read, write, make directories, etc.  So the problem is with my computer--not the remote one.

Now, if I add the option uid=MYID, I can read and write just fine.  The system makes me the owner of the directory on mounting.  But that's not what I want--I'm trying to allow multiple users access to this file system.  I want there to either be a neutral owner (e.g. root) with others having read/write access, or I want the owner of the mount point to be the user currently logged in.  How can I modify my fstab to allow this?

Thanks,
Adam

---

### Post by bict on 2010-08-17
Hey, try setting fmask=122 and dmask=122 because the masks are in reverse of e.g. when you set chmod. See the link for explanation: [http://en.wikipedia.org/wiki/Fmask](http://en.wikipedia.org/wiki/Fmask)

good luck

ps: fmask and dmask seems to be deprecated, you can use file_mode or dir_mode instead (e.g. file_mode=0777,dir_mode=0777)
you can find a short explanation here: [http://www.tectite.com/fmdoc/file_mode.php](http://www.tectite.com/fmdoc/file_mode.php)

---

### Post by aasmith on 2010-09-14
I'm sorry--I hadn't noticed that someone replied.

Good guess, but it didn't work. Same problem as before--I can access it when I su or sudo, but not as myself.

Any other thoughts?

---

### Post by elico on 2010-09-14
cifs are windows client...
so if the server is a linux one there is a problem with multiple users permission on samba.

i posted on this matter before.

i ubuntu server and there is a problem for the samba system to write on the share or access it using the login information you are trying to access the share.

i just thought  about the option that you can defined the uid=%u or whatever the user name variable is.(on the server)
but im not sure it will work.

---

### Post by dmizer on 2010-09-15
Please have a look at the second link in my sig. There is a troubleshooting section which will address the permissions problems you are experiencing.

---

### Post by IcarusR on 2010-09-30
Don't know if you've sorted this or not ?

I believe you need to approach this in a different way & define users who have read & write perms in your /etc/samba/smb.conf file on the server.

See the smb.conf man page for details but the relevant options are

read list
write list

---

