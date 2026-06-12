---
title: "I fail at Linux Neworking"
date: 2008-05-08
forum: Mythbuntu
---

### Post by Caps18 on 2008-05-08
All I am trying to do is share 4 folders on my Mythbuntu computer with my Linux Mint laptop.  I am trying to use Samba because I didn't install NFS the first time and now it won't install from the control center...

It looks like the folders are shared using a mythtv user account, but I have only created a mythbuntu and my_name user accounts and smbpasswd -a & -e user accounts.  It doesn't like me making a mythtv user account on my linux mint computer...

Is there a simple step-by-step tutorial out there on how to setup Samba networking.  I know it is all powerful and secure, but I need it to work.
[http://ubuntuforums.org/archive/index.php/t-2389.html](http://ubuntuforums.org/archive/index.php/t-2389.html)
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server)
and my linux book are all about the same.  They tell me all about the smb.conf file, but not how to make it work or fix problems that I have.

Thanks.

---

### Post by CleverJake on 2008-05-08
Ive had a similar problem, only with my windows machine.

Can anyone say for a fact if mythbuntu can network with a non myth box?

---

### Post by Caps18 on 2008-05-08
I was able to get it working in Windows.  There was nothing to do in Windows, and just setting up shared folders and installing Samba.

But now I switched to linux and this is the only thing I haven't been able to get working.

---

### Post by volkswagner on 2008-05-08
Have you tried?

```
sudo apt-get install nfs-common nfs-kernel-server
```

---

### Post by Caps18 on 2008-05-08
Not yet.  I guess I could switch to NFS instead of Samba since I don't have any Windows computers.  I have NFS setup on my laptop already (hopefully correctly), I'll have to see if I can get Mythbuntu to work with NFS tonight I guess.

---

### Post by prosonik on 2008-05-08
Hi,

I'm a little confused at what's going on.. So What version of mythbuntu are you using? What are version of mint are you using? Currently, my setup @ home is mythbuntu 8.04, and i have a couple other pc's running vista/ubuntu etc. They can all see the mythbuntu box fine. Actually, i was surprised at how well, it worked. remember, with Samba the authentication is specific to the machine your logged into. so if you are on pc A) and trying to logon to pc B) you must have the credentials to logon to pc B). I belive to get basic install going on mythbuntu, just go to the mythbuntu control center, enable samba, and you should be on your way. If you have already done that, and things are still funky,
please post your your /etc/smb.conf from your mythbuntu box. Also, this may sound stupid, but are both the machine running on the same network? Are you running either one of them in VM or something like that?

prosonik





> **Caps18 said:**
> All I am trying to do is share 4 folders on my Mythbuntu computer with my Linux Mint laptop.  I am trying to use Samba because I didn't install NFS the first time and now it won't install from the control center...

It looks like the folders are shared using a mythtv user account, but I have only created a mythbuntu and my_name user accounts and smbpasswd -a & -e user accounts.  It doesn't like me making a mythtv user account on my linux mint computer...

Is there a simple step-by-step tutorial out there on how to setup Samba networking.  I know it is all powerful and secure, but I need it to work.
[http://ubuntuforums.org/archive/index.php/t-2389.html](http://ubuntuforums.org/archive/index.php/t-2389.html)
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server)
and my linux book are all about the same.  They tell me all about the smb.conf file, but not how to make it work or fix problems that I have.

Thanks.

---

### Post by Caps18 on 2008-05-08
I am running mythbuntu 7.1 and Linux Mint 4.  I was happy with how easy it worked when I was using my old XP laptop to connect to the mythbuntu box.  And I'm sure this will work fine once it is setup correctly.  The user authentication thing is probably what is happening.  The owner of the folders on the mythbuntu box that I am trying to share is mythtv.  But mythtv can't login to the linux mint laptop (I'm not sure what the password it uses is either, or if it needs to be the same).  And it won't let me add the mythtv account using smbpasswd -a (possibly because I don't have that user account...?) 


I was looking through the smb.conf file on both computers yesterday, and I'm sure that there is something not quite right there.  But, I still am thinking it is an authentication issue currently.

I will work on it some more tonight, and it will work. :twisted:

---

### Post by prosonik on 2008-05-08
Okay, 

Now I understand some more, it's Linux Mint that's causing the issue.
First off, if you know the your smb.conf works on your mythbox
copy it over to your mint box, and modify the paths to whatever..

Now, also make sure that samba is actually installed on Mint!

Once you are SURE you have samba install (sudo apt-get install samba)
try it again

prosonik

---

### Post by Caps18 on 2008-05-09
Yea!, I got NFS to work...

:)

But for some reason I had to specify a range of IP addresses that had access to the folder instead of the exact IP address that my laptop has.  For example in my /etc/exports file

/path/to/shared/files 192.168.1.142(rw,no_root_squash,async)  doesn't work
/path/to/shared/files 192.168.1.0/24(rw,no_root_squash,async) works

My laptops IP is 192.168.1.142 and I can ping it successfully from the mythbuntu computer.

Now I just have to deal with all these permissions for files belonging to mythtv (they were made on the mythbuntu box)...

---

