---
title: "Samba share issues on new install"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by driscollw on 2011-01-22
I have installed ubuntu 10.10 and the Samba addon to configure my shares to my Windows terminals. 

This is what I got
Firewall off (utf disabled)\
Internal Sata /dev/sda1 (EXT4 FS)
External USB HDD /dev/sdb1 mounted at /media/SG1500GB (EXT4 FS)

I have two shares 

1. //home/test - Which I can see and access with no problems (can't write to it though even though I set the share as writable?, but, I can read from it). This is available to everyone. My windows terminal can see this folder and access it. This is on my main 80GB internal drive /dev/sda1. 

2. //media/SG1500GB/Music. I set this up for everyone full access and I can see it at all my Windows machines but, I can't get into the folder. Windows keeps giving me an error stating network path not found. I also try to access it via the Nautilus (Places/Network/system/music) and get an error message "unable to mount location, Failed to mount windows share". This drive is mounted per the disk utility. 

Any help would be greatly appreciated. If anyone needs anymore information please let me know. 

Thank you for your time.

---

### Post by driscollw on 2011-01-22
I am still having issues. I am starting to believe I am only having sharing problems on the USB Drive. I was thinking about turning off the automount and just edit the fstab to mount the drive to something like /mnt/SG1500GB to see if that would work. Other than that I am stuck.

---

### Post by iiDopDop!! on 2011-03-28
I am also having the exact same problem, if u get any news or end up figuring out what was wrong I'd be glad to know

---

### Post by The Guv. on 2011-03-29
I'm also having an issue with a fresh 10.10 install and samba (nothing else added or removed).

I can see all of my folders, but I cant get in to any of them, I have a 'Shared' folder which is meant to be able to be accessed by everyone inc guests but no luck, can't even access using user/password.

And then I've got a handful of user folders which I can't access without having to add the USERNAME to every entry possible and manually setting the folder permissions to 0775.

As I'm building a NAS for a small business client to use, it can't be this complicated as they'll want to add and remove users themselves and at the moment I'm struggling!!

---

### Post by Morbius1 on 2011-03-29
So far every post I've read has nothing to do with Samba and everything to do with Linux file permissions.

Let's take the original post as an example ( although by this time I think the OP has moved on ).

> 1. //home/test - Which I can see and access with no problems (can't  write to it though even though I set the share as writable?, but, I can  read from it). This is available to everyone.OK, so he set up a new directory using say ... "sudo mkdir /home/test". He may have even changed ownership to his own username say  ... bob : "sudo chown bob /home/test"

That's going to create a folder owned by bob with permissions of 755. Bob can read and write and everyone else can only read. The fact that he set the samba share to allow write will not override the Linux permissions on the folder itself.

The second thing is he needs to define exactly what he means by "write". A write to a directory means to add to or delete from that directory. A write to a file means the ability to edit the contents of that file.

If he wants everyone to add or delete files from that directory then he needs to change permissions:
```
sudo chmod 0777 /home/test
```If he wants everyone to do the above and also be able to edit the contents of it's files then things can get a bit more complicated. If this is a peer-to-peer type of situation where bob wants to share /home/test to mary then the simplest way is to add a line to the share definition like this:
```
[test]
path = /home/test
read only = No
guest ok = Yes
[COLOR=Blue]force user = bob[/COLOR]
```"bob" is the local login user of the machine that has the /home/test share. When the guest accesses the share his/her identity will be converted to bob. Everything that mary adds to the share will save as owner = bob so everyone will be able to edit everyone else's files.

In any event no one here told us what method they are using to create the Samba share. There are two methods ( Usershare - a.k.a. Nautilus-share ) and Classic-share. Their share definitions are in two different places and are handled differently. So it's always best to post the output of the following commands when asking for help:
```
net usershare info --long
testparm -s
```It would have been a good idea to post the permissions on all the target folders as well so responders could assess how to change permissions to accomplish the desired requirement.

[COLOR=Blue]EDIT[/COLOR]: @The Guv, your requirements are so different from the rest that it really warrants a separate post in my opinion.

---

