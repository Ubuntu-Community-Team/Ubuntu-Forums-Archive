---
title: "Permanently Mount Samba Shares"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by brent1975 on 2013-01-22
Hello I am currently trying to mount a few shares on my Ubuntu Desktop and having a bit of a problem. I just reinstalled Ubuntu  and this was working previously. 

I have a Ubuntu 12.04 server sitting in the basement that houses all my media, documents etc...  

I have a desktop that has Ubuntu 12.04 and I am able to connect to the  share manually using the connect to server method.  So I was wanting to  mount these specific drives so that they would be there even after I  reboot the computer.

I did some reading and came up with this method.

I installed samba from the appstore.
I created a few folders in /media called brent,music,movies,www
I opened up /etc/fstab and modified it with adding the following at the bottom

```
//192.168.2.105/Movies /media/Movies smbfs credentials=/etc/samba/cred-file,uid=brent,gid=users 0 0

//192.168.2.105/Music /media/Music smbfs credentials=/etc/samba/cred-file,uid=brent,gid=users 0 0

//192.168.2.105/Brent /media/Brent smbfs credentials=/etc/samba/cred-file,uid=brent,gid=users 0 0

//192.168.2.105/WWW /media/WWW smbfs credentials=/etc/samba/cred-file,uid=brent,gid=users 0 0
```

I then created a file in /etc/samba/cred-file and made my credentials.
```
username=brent
password=password
```
saved and did a sudo mount-a from terminal and I get 4 password prompts each time I put in the password a drive will mount. 

I am used to putting in a password when ever I do anything sudo related  but 4 times for each drive seem something is messed up.... 

I have tried this on a windows box and mounts fine. so I know its not  something wrong with my samba server with permissions. It seems that it  is not seeing the cred-file for some reason.  Any one have an Idea. Open  for Ideas or suggestions..

Thank you in advance,

--Brent

---

### Post by SeijiSensei on 2013-01-22
You're missing the "-o" before the "credentials" keyword.

However I'd strongly recommend you use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") instead of SMB to share files between *nix machines.  You'll have much better performance, particularly if you're trying to play video files with something like mplayer.

---

### Post by dannyboy79 on 2013-01-22
also, if you're going to stick with samba, use cifs instead of smbfs

---

### Post by brent1975 on 2013-01-22
> **SeijiSensei said:**
> You're missing the "-o" before the "credentials" keyword.

However I'd strongly recommend you use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") instead of SMB to share files between *nix machines.  You'll have much better performance, particularly if you're trying to play video files with something like mplayer.

I don't recall putting the -o in there? hmm  I would look into how to use NFS instead.

Is there another method I can use to mount drives in ubuntu permanently instead of using samba?

---

### Post by brent1975 on 2013-01-22
> **dannyboy79 said:**
> also, if you're going to stick with samba, use cifs instead of smbfs

So which is better NFS or CIFS?

---

### Post by brent1975 on 2013-01-22
You have mentioned if I choose to use samba. That sounds as if there is another alternative. What are these other alternatives?

would these alternatives be client side or server side?

---

### Post by dannyboy79 on 2013-01-22
NFS is network file system. It's the preferred method AFAIK when sharing files between all *nix computers. There's a great guide on the forums some where, just search for it.

Samba is really the file sharing protocol when sharing files in a windows environment, again as far as I know.

---

### Post by brent1975 on 2013-01-22
Unfortunately my kids have Windows 7 on 2 desktops and 2 laptops. And they need access to there shared drives.  I will eventually move there devices over to ubuntu. But I want to make sure I know how to properly configure a desktop before putting them out of commission for a period of time .  My kids without facebook or there music is the end of the world. 

The have there own home drives Music Photos and documents drives which they are used to using and use them alot.

While I was looking into CIFS I came across this. Naturally I added my own information. 

//192.168.2.105/Movies /media/movies cifs iocharset=utf8,credentials=/etc/samba/.cred-file,uid=1000 0 0

I added this to the fstab and I am still getting the same problem when I do a sudo mount-a it is asking me for the credentials. Once I put in the password the share will show up.  I even rebooted the system wondering if it would mount on startup and still no go...  It's almost as if it's not using the .cred-file for the credentials.

---

### Post by dannyboy79 on 2013-01-22
you're missing the auto option. it should read

```
//192.168.2.105/Movies /media/movies cifs auto,iocharset=utf8,credentials=/etc/samba/.cred-file,uid=1000 0 0

```

---

### Post by brent1975 on 2013-01-22
I finally got it to work. I had to install smbfs. which I guess is not part of the package when you install samba from the app store...

All is well...  Thanks alot.

---

### Post by SeijiSensei on 2013-01-22
> **brent1975 said:**
> Unfortunately my kids have Windows 7 on 2 desktops and 2 laptops. And they need access to there shared drives.  

I run both NFS and Samba on my server.  They work fine in parallel.

---

### Post by dannyboy79 on 2013-01-22
> **SeijiSensei said:**
> I run both NFS and Samba on my server.  They work fine in parallel.
me also

---

### Post by dmn_clown on 2013-01-23
> **SeijiSensei said:**
> I run both NFS and Samba on my server.  They work fine in parallel.

How do you reconcile the difference between ACLs?

---

### Post by SeijiSensei on 2013-01-23
> **dmn_clown said:**
> How do you reconcile the difference between ACLs?

I'm not sure I understand the question.  Both servers export the same ext4 file system that has normal Unix permissions.  I do not know how Samba handles Windows-style ACLs because I never use them.  I just log in to the share with a username and password that Samba manages.  It offers a variety of options for mapping from those credentials to permissions on the underlying ext4 filesystem.

---

### Post by dannyboy79 on 2013-01-23
i think he thinks the same share is both shared out as NFS and SAMBA. i am not sure though

---

### Post by aaronjsmith21 on 2013-01-23
It takes some doing to get Windows ACL's to work correctly, or so I have found, here is posting about it:
[http://serverfault.com/questions/212000/can-samba-support-full-windows-acls](http://serverfault.com/questions/212000/can-samba-support-full-windows-acls)

It covers on how it could be setup to support it via Samba Shares.

I hope this is in some way helpful.

~Aaron J Smith

---

### Post by aaronjsmith21 on 2013-01-23
Oh, after looking over the question again, I am not sure that is possible to do so to have the ACL's transfer over from one to the other (NFS to Samaba and vice versa), but I could be wrong.

I think that would take some real doing, including some scripting of some sort...

I guess I am not sure about the question either.

---

### Post by SeijiSensei on 2013-01-24
It is certainly possible to have the same directory shared with both NFS and Samba.  I share home directories that way all the time, but as I said I just use standard authentication and permissions with no ACLs.

---

### Post by dmn_clown on 2013-01-27
> **aaronjsmith21 said:**
> Oh, after looking over the question again, I am not sure that is possible to do so to have the ACL's transfer over from one to the other (NFS to Samaba and vice versa), but I could be wrong.

I think that would take some real doing, including some scripting of some sort...

I guess I am not sure about the question either.

According to Jeremy at samba it is possible:  [http://lists.samba.org/archive/samba/2011-October/164668.html](http://lists.samba.org/archive/samba/2011-October/164668.html)

The NFS4 ACLs inherit the NT ACLs on the share with the suggested configuration.

---

