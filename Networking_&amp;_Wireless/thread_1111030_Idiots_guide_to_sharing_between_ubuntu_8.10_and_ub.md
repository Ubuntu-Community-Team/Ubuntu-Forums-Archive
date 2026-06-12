---
title: "Idiots guide to sharing between ubuntu 8.10 and ubuntu 8.10 needed"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by paranoidandroidz on 2009-03-30
I ve had so much trouble doing what I assumed would b so easy. I ve bin tryin for days and i am just about to give up.

So my last attempt, I have just freshly installed ubuntu 8.10 on the two laptops both using wireless, I just want to be able to share files between the two. 

I ve had so many problems, and so many guides saying to do this and that, I jus wonder if anybody would be kind enough to talk me through it from the very start.

---

### Post by Iowan on 2009-03-30
Dunno if I can offer a talkthrough, but...
How are you sharing files - Samba?  NFS and SSHFS are a couple more options.  I can provide links to [http://help.ubuntu.com](http://help.ubuntu.com) articles if you'd like.

---

### Post by paranoidandroidz on 2009-03-30
Thanks for your reply, I just want to use nautilus, I really dont want to back down the other routes you mentioned, In the past I have been able to sumtimes c the folders but never access them from the other computer

---

### Post by paranoidandroidz on 2009-03-30
Lmao

Hey thanks anyway but I got there, I ve tried the same thing at least 10 times, and all of a sudden it works, must b the fresh installs.

---

### Post by megamania on 2009-03-30
> **paranoidandroidz said:**
> Thanks for your reply, I just want to use nautilus, I really dont want to back down the other routes you mentioned, In the past I have been able to sumtimes c the folders but never access them from the other computer

There should be no need for NFS or Samba. Try mounting it just like you would mount any device. If the remote computer's address is 192.168.1.2, mount it with something like

sudo mount [your options] 192.168.1.2/home /mnt/my_remote_disk

I did it some time ago and it worked flawlessly. Let me know if you need the correct syntax (I'm not at home now).

---

### Post by paranoidandroidz on 2009-03-30
cheers for your reply megamania

Would that option work if im trying to share an external drive over the network as well?

---

### Post by Iowan on 2009-03-30
There's a nice How-To on **fstab **around here somewhere - I'll see if I can find it...

---

### Post by hovzio on 2009-03-30
I guess security is also an aspect that should be looked at. If you are only transfering data on a lan that is behind a firewall/router etc. then its somewhat safe to rely on unencrypted protocols and software (ftp..). I personally prefer the above mentioned sftp and sshFS. They are said to be secure. Correct me if I'm wrong; nautilus does rely on some type of underlying file sharing software, whether its connecting via sshfs, sft, ftp, NFS, samba..Something has to be "serving" the files etc. Somewhere seahorse comes in play.One of them is being used by nautilus. In my opinion, if you are looking to do things over the internet I definatley recommend using a secure method of transfering files.:)

---

### Post by megamania on 2009-03-30
> **paranoidandroidz said:**
> cheers for your reply megamania

Would that option work if im trying to share an external drive over the network as well?
As long as the drive has an ip address, why wouldn't it work?

This is what I used to mount my home partition on my secondary box:

sudo mount -t nfs 192.168.1.3:/home /media/mule

so you probably need to install:
_client side_
sudo apt-get install portmap nfs-common
_server side_
sudo apt-get install nfs-kernel-server nfs-common portmap

I'm no expert, but this worked perfectly for me.

---

### Post by paranoidandroidz on 2009-03-30
great stuff, cheers i'l give it a go


Thanks for all your replies, certainly given me some options I wasnt aware of, wish i'd jus posted here first instead of going bald first ;)

---

### Post by inobe on 2009-03-30
> **paranoidandroidz said:**
> Thanks for your reply, I just want to use nautilus, I really dont want to back down the other routes you mentioned, In the past I have been able to sumtimes c the folders but never access them from the other computer

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

i didn't read the rest of the posts, this one i am replying to seems to justify the link.

---

### Post by Iowan on 2009-03-31
The **fstab** [link]("http://ubuntuforums.org/showthread.php?&t=283131") I promised.

---

