---
title: "Mounting folders between  Ubuntu-Xubuntu laptops"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by kartal on 2009-11-06
Hi

I have been researching and trying multiple methods to mount some folders from my Ubuntu laptop to my Xubuntu netbook. So far I have tried(and some similar methods)

sudo mount /source /target (-o username=usname,password=pass)
sudo mount -t cifs /source /target (-o username=usname,password=pass)

source(Ubuntu laptop)=//192.168.2.102/username 

target(Xubuntu netbook)=/home/username/Desktop/mount

I have the same user defined on my Ubuntu laptop, added to the users group). My user on the target laptop is also an admin user with a password. I also tried adding it to the fstab which did not produce any result. I can use "sshfs" to mount stuff , that one works but for some reason simple network folder mounting does not work. 

here is a sample error message
"
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
"



I did read many pages online, most of them offers similar methods, and most of them seems to assume that a mounting happens to be between an Ubuntu pc and a Windows share.

Btw I can mount shares from a Windows pc on my netbook, so my netbook has all the tools necessary to run a successful sharing and accessing session.

Any suggestions?


thanks

---

### Post by kartal on 2009-11-06
Any insight on this issue?


thanks

---

### Post by pearldrums on 2009-11-23
I by far am not the expert (as i'm trying to figure this out right now as well), but here is a thread on the topic:

[http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)

I'm sure it has the info your looking for, but unfortunatly it was started in like 2006, and theres 20 pages to wade through for current information... If you figure out the currently accepted method I'd urge you to add an edit on to your first post including the date and either what the current method is or a link to a specific post with a work around. I'll re-post if I figure anything else out.

---

### Post by pearldrums on 2009-11-24
Also, I posted this in that thread as well, but keep in mind that if you have a shared folder in your Xubuntu computer, you can access it from your Ubuntu computer. This may not be as convenient, but it will get the job done. If you don't already have a shared folder I can offer some suggestions on how to create one, but the only thing I've actually done was create one in ubuntu, and then change over to Xubuntu, which is a lot of work to make a little file.

---

### Post by kartal on 2009-11-24
Hi

Thanks for the follow up. 

I can share between my xubuntu and windows no problem. But for some reason having hard time getting Ubuntu work. I will keep this post alive when I have a solution as well

thanks

---

### Post by dmizer on 2009-11-24
See the 2nd link in my sig. You can use that method for mounting shares on Xubuntu.

---

### Post by kartal on 2009-11-24
@dmizer

Thanks for the suggestion. I have done most of what you have in your post already and I can access to Windows shares no prob. 

My problem is neither seeing the windows shares under Ubuntu nor seeing xubuntu shares under Ubuntu. My problem is that I cannot see Ubuntu shares under Xubuntu or Windows. It works one way only at the moment.

---

### Post by dmizer on 2009-11-24
Please post your /etc/samba/smb.conf file from the Ubuntu computer.

Also from the Ubuntu machine, please post the output of:
```
sudo iptables -L
```

---

### Post by kartal on 2009-11-24
Hi
here is the camba config

[http://pastie.org/713357](http://pastie.org/713357)


sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by dmizer on 2009-11-24
Where did you find the howto for that smb.conf file?

---

### Post by kartal on 2009-11-24
dmizer

I am not sure where I have found it but I do not think I modified my samba config that much myself, because after getting things working well between Windows and Ubuntu, I did not modify it at all . Last week I I haev used "Gadmin-Samba" tool to see if any Gui tool might help me out sharing folders on my Ubuntu installation and I did not get any success.

---

