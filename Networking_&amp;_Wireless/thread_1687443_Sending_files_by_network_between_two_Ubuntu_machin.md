---
title: "Sending files by network between two Ubuntu machines"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by Daanii on 2011-02-13
My two machines are both running Ubuntu 10.10. I want to transfer program files between them using a local area network. 

My Ubuntu machines can both see the Window machines on the network, and get files from them. But my Ubuntu machines do not detect each other as being on the network. Nor can my Windows machines detect my Ubuntu machines. 

From what I can tell, that's normal, and I've become resigned to using a pendrive to transfer files between the two machines. Or even sending files as email attachments. 

But I'm posting this in the hope that I'm wrong, and that there is a clean and easy way to transfer files between two Ubuntu machines on the same local area network. 

Thank you.

---

### Post by infamous-online on 2011-02-13
Do you have Samba enabled on your Ubuntu machines? If not enable that and you'll be able to share files between Windows and Ubuntu. You may have to edit the file as well to get it setup the way you like, however I'd refer to the docs on that.

---

### Post by Bucky Ball on 2011-02-13
I personally use:

Places>Connect to Server>SSH.

I then input the IP of the machine I'm wanting to connect to, you will be asked for a password, input password of the machine your trying to get to, and you're in. Share away!

I am using static IPs though. This may also be possible with using the computer name. Not sure, never tried it. ;)

To me, Samba is a bit of a dog's breakfast.

---

### Post by Daanii on 2011-02-13
> **infamous-online said:**
> Do you have Samba enabled on your Ubuntu machines? If not enable that and you'll be able to share files between Windows and Ubuntu. You may have to edit the file as well to get it setup the way you like, however I'd refer to the docs on that.

I'll check into Samba in a couple of hours when I get on my Ubuntu machines again. (I'm now on Windows.) 

But I want to confirm one thing. I don't want to do anything between Windows and Ubuntu machines. I just want to send files from one Ubuntu machine to the other Ubuntu machine. Do I have to use Samba for that?

---

### Post by cjhabs on 2011-02-13
In my experience, while you can use samba for that, it is slow compared to using NFS.

Share data drive via NFS
Need to install NFS server - this also installs client support
sudo apt-get install nfs-kernel-server nfs-common portmap
sudo vi /etc/exports
	/path_to_share 192.168.1.1/24(rw,no_root_squash,async)
# where 192.168.1.1 is ip of nfs server
sudo /etc/init.d/nfs-kernel-server restart

Also you can use rsync instead - which is a very efficient protocol:
rsync -au source dest

---

### Post by nickleboyblue on 2011-02-13
You know, there is a more "standard" Ubuntu way of doing this that is built into the right-click menu for files on your Ubuntu computers.  Just right-click, find the item called "Sharing Options," and enable file sharing.  You will be asked to logout and log back into your account.

If you do things this way, you don't have to worry about what program you're using unless your needs require faster speeds than what is necessary for watching an HD video on one computer from a file that is on another computer without lag.  The best part about it?  It's easy to set up and it's built-in to Ubuntu's system (once enabled).

Cheers!

---

### Post by inobe on 2011-02-13
> **Daanii said:**
> 

But I'm posting this in the hope that I'm wrong, and that there is a clean and easy way to transfer files between two Ubuntu machines on the same local area network. 

Thank you.

it is easy [http://www.youtube.com/watch?v=89hjWOb8qmY](http://www.youtube.com/watch?v=89hjWOb8qmY)

older video but good.

---

### Post by imercury on 2011-02-14
SOLVED - meaning there is _[COLOR=Red]no easy way to link two computers on Ubuntu [/COLOR]_-Even to file share is a pain in the butt,
 If it wasn't so sad it would be 'two' funny  for words.  Of any OS to call itself an OS   needs to make this easy -PERIOD - 
FYI see another thread on this [B]conneting 2 ubuntu computers EASILY!!!!

[/B]

---

### Post by 3177 on 2011-02-14
> **infamous-online said:**
> Do you have Samba enabled on your Ubuntu machines? If not enable that and you'll be able to share files between Windows and Ubuntu. You may have to edit the file as well to get it setup the way you like, however I'd refer to the docs on that.

NOT SOLVED

+1 


have you actually tried Samba yet?
I have an XP machine and an Ubuntu 10.10 machine.
I needed Samba to do axactly what your talking about.
Dont give up.
Ubuntu always has a workaround.
And SAMBA IS YOURS

---

### Post by jonandrews on 2011-02-14
File sharing is easily achieved with just a few mouse clicks in most cases, even between operating systems. I have put an illustrated step by step guide here....

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by Morbius1 on 2011-02-14
Although I have no preferences either way on what method of samba is used there are advantages in the method ( called nautilus-share,thunar-share or usershares ) outlined in jonandrews's HowTo.

* It will install all the samba server packages automatically when first used so you don't have to guess which ones to install.
* It's almost Windows like ( Windows Simple Sharing ) in how you create shares.
* It will automatically modify linux file permissions to make sure that linux permissions and samba access permissions is in sync. This step usually trips up users of the Classic method. 
* You can create and delete shares in seconds without restarting the samba services.

---

### Post by SeijiSensei on 2011-02-14
There is the tried-and-true method of using scp:

```
scp /path/to/my/file user@machine:/path/to/destination
```

If you know the remote user's password, or you have shared SSH keys set up, this is just like copying from one directory on your local machine to another.

As someone else suggested, rsync is a very efficient way to transfer lots of files between Linux hosts.

Neither of these methods require setting up NFS or Samba or any other file-sharing service on the machines.

---

### Post by raequin on 2011-03-06
> There is the tried-and-true method of using scp:

```

scp /path/to/my/file user@machine:/path/to/destination
```
If you know the remote user's password, or you have shared SSH keys set up, this is just like copying from one directory on your local machine to another.

Can you explain how this works for two computers sharing a wireless router?  Don't I need to know the IP address of the other computer or something?  I tried the code above, substituting "user@machine" with the name appearing on the other computer in terminal (like on mine its "rae@rae-laptop") and it did not work.  This was the result.
```
ssh: Could not resolve hostname laura-T-6836: Name or service not known
lost connection
rae@rae-laptop:~$ 
```

I'd like to be able to use the simple scp option since I only want to share files occasionally.

---

