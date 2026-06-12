---
title: "Network Sharing - Tutorial?"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by Vi3GameHkr on 2010-05-16
Hello,

Could anyone direct me to a tutorial on sharing files over a network between two Ubuntu systems?  One is a desktop machine running 10.04, and the other is a laptop running 9.04 (I can't be bothered to upgrade just yet, it's a 2-3 hour download)

I've tried a few things myself, but Ubuntu, unlike Windows, doesn't seem to be much of a DIY system, because everything is too hard to figure out and every machine and scenario is different.  What I have tried: I tried setting up NFS by adding
```
/home/marcus/Projects marcus-laptop(rw,async)
``` to /etc/exports on the desktop (server) and then adding ```
marcus-desktop:/home/marcus/Projects /home/marcus/Projects nfs rsize=8192,wsize=8192,timeo=14,intr
``` to /etc/fstab on the laptop (client) but then when I try typing ```
sudo mount marcus-desktop:/home/marcus/Projects /home/marcus/Projects
``` in Terminal on the laptop, I get "mount.nfs: mount system call failed."

I also tried setting up Samba, so I downloaded the Samba package from the software list on both computers, I figured out how to add a folder to share but couldn't figure out how to access it from my laptop.

Some detailed explanations, or links to good detailed tutorials would be great because, as is quite obvious, I suck at Ubuntu.

I've questioned whether Ubuntu is really for me recently, because for every 3 hours I spend trying to make something possible on Ubuntu, I can do that same thing in minutes on my Windows set up.  I've heard once I've improved my programming skills, I can customize programs to my liking to make them easier for me to use, or add features I like to existing programs so I don't have to completely rewrite that program, I mean afterall that's what free open-source is for right?

---

### Post by Vi3GameHkr on 2010-05-18
Okay, I read a few things and figured out exactly what I want to do, and I wonder if this thread belongs here too, but I would appreciate any help I can get.

I want to get a small cloud computing system going here, but I don't want a dedicated server or anything.  I have a desktop and laptop, both are on the same network.  I just want the laptop to be able to access the files that are stored on the desktop, and edit them without having to download, edit, save, re-upload and all of that.  If it does download and re-upload, I would like that to be automatic.

If possible, I also want to have local copies of all the files on my laptop so that when I am away from home I can still access them.

My ideas so far include using NFS, but I wouldn't know how to set that up (I've already tried a few tutorials)

---

### Post by Vi3GameHkr on 2010-05-18
I'm really struggling here.  I wish I could do this myself, and I haven't found anything about file sharing in any of the ubuntu books I've checked out.  I was wondering if I could do anything with SSH.  Would I be able to use that to use files, but leave them on the server?  Even if I can't, would it be easy? It sounds pretty secure anyways, and it sounds like I can use it over the internet.

---

### Post by drdos2006 on 2010-05-18
You need to set up both machines with a group name common to both machines.
Use "System" - > "Administration" - > "Users and Groups" on each machine.
Add a group name. (If you cannot add a group name from the GUI, then use the Command Line Interface from a terminal and type:
groupadd groupname.

Add both users to the group name, that is your laptop and desktop names.
Use samba to access a shared folder.
Edit the samba config file to add your groupname.

regards

---

### Post by lisati on 2010-05-18
Here's a tutorial I have followed in the past: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by Vi3GameHkr on 2010-05-18
haha third time is the charm.

Thanks a whole lot guys.  drdos2006, the imaginary progress bar just jumped from 20% to 60% with that. Thanks.  And lisati, I had seen that tutorial in the past, but I wasn't entirely sure if it applied to my situation.  I have both machines dual-booting Windows, but I don't need to share any files with Windows at all.

Thanks a whole lot, I'll let you know how things go from here.

[EDIT] Okay I'm getting an error again.  That tutorial was written for Dapper 6.06 I guess, so when I type /etc/init.d/samba stop or /etc/init.d/samba start I get "sudo: /etc/init.d/samba: command not found"  I'll probably figure this out on my own, but still nice to get help

---

### Post by 99_rover on 2010-05-18
Vi3GameHkr

Keep the thread going - be really interested in how you progress - trying to do the same thing and running into the same issues.........

---

### Post by drdos2006 on 2010-05-18
If you want to use Network File Sharing, you need a server machine and a client machine. The only other way I have been able to share Linux files is with Samba.
I am using Ubuntu 9.10 64 bit and 32bit on an old P4. I did find that I was able to have Ububtu 9.10 32bit change the permissions automatically, but I needed to tweak Ubuntu 9.10 64 bit with CLI operations. Still need Samba tho.


regards

---

### Post by Vi3GameHkr on 2010-05-18
At this point, I think I've got my desktop all set up to share some files, but I am unsure of how to access them from my laptop.  When I go to Places->Network from my laptop, I get "Could not display "network:///".  Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply.  possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.  Please select another viewer and try again."

That happened on 9.04, on 10.04 on my desktop, I didn't get that though.

[EDIT] And btw, [the tutorial that lisati suggested]("http://ubuntuforums.org/showthread.php?t=202605") worked very well for setting up the server.. At least so far, but it doesn't explain using Ubuntu as a client as well.

[EDIT] Well this is kind of weird, but I tried again and didn't get that extremely long and meaningless error.  In the file browser, however, I couldn't see anything but "Windows Network" and clicking that got me "Unable to mount location  Failed to retrieve share list from server"  On my desktop, I see all the machines on the network except for my laptop too.

---

### Post by 99_rover on 2010-05-18
Ok I am using Lucid 32 on two machines one P4 and one older P3 just to get the bugs out. Have samba on both and have a common group name on both. Updated the smb.conf to include the group name.

Next??

---

### Post by drdos2006 on 2010-05-18
Yo may need to own the share on the desktop by using sudo chown on the desktop.
I am assuming that you were able to make a shared directory using Samba.
Make sure your group and user name are functioning properly before changing ownership.
Try this from your desktop:
sudo chown -R theuser /path/to/newdrive
sudo chmod -R 777 /path/to/newdrive
sudo chgrp thegroup /path/to/newdrive
regards

---

### Post by Vi3GameHkr on 2010-05-18
Do you need a smb.conf on both machines?  How do you find if you are using 64-bit or 32-bit? I honestly forget which one I installed.

I think my problem is that my laptop is like virtually invisible to the network, because I can't see the laptop on the network from any of the machines (except on the router) and on my laptop, I can't see any other machines.  That's kind of weird because I got synergy to work between my desktop and laptop.  I got something called smb4k and on my laptop, if I go to the network neighborhood tab, it shows nothing.  On my desktop it shows WORKGROUP with all the computers except my laptop, just like in the File Browser.

[EDIT]drdos2006, I did sudo chmod 0777 /home/files  Is that good enough?

---

### Post by drdos2006 on 2010-05-18
You need Samba on both machines. You need to edit /etc/samba/smb.conf on both machines to change the workgroup to MyUserGroup.

My desktop core2duo is a 64bit motherboard, I use Ubuntu 9.10-64bit.
My second machine is not a 64bit motherboard, I use 32bit Ubuntu 9.10.

Yes for the Desktop /home/files directory being 0777.

As I stated ealrlier, my 32bit machine running Samba changes permissions automatically when sharing but not my 64bit desktop.
Which is why I had to use chmod to change my share permissions.

regards

---

### Post by Vi3GameHkr on 2010-05-18
My problem at this point is simply that my laptop isn't showing up, and on my laptop, I can't see any other network machines.  I am absolutely certain they are on the same network though.

---

### Post by drdos2006 on 2010-05-18
From a terminal on your desktop, type: ifconfig
From your laptop, type : ifconfig
From your laptop, can you type : ping desktopIP
( Press Control-z to stop)

regards

---

### Post by Vi3GameHkr on 2010-05-18
Pinging works both ways

> marcus@marcus-laptop:~$ ping 192.168.0.3
PING 192.168.0.3 (192.168.0.3) 56(84) bytes of data.
64 bytes from 192.168.0.3: icmp_seq=1 ttl=64 time=1.41 ms
64 bytes from 192.168.0.3: icmp_seq=2 ttl=64 time=1.54 ms
64 bytes from 192.168.0.3: icmp_seq=3 ttl=64 time=2.46 ms
64 bytes from 192.168.0.3: icmp_seq=4 ttl=64 time=1.56 ms

> marcus@marcus-desktop:~$ ping 192.168.0.7
PING 192.168.0.7 (192.168.0.7) 56(84) bytes of data.
64 bytes from 192.168.0.7: icmp_seq=1 ttl=64 time=1.32 ms
64 bytes from 192.168.0.7: icmp_seq=2 ttl=64 time=1.50 ms
64 bytes from 192.168.0.7: icmp_seq=3 ttl=64 time=1.40 ms
64 bytes from 192.168.0.7: icmp_seq=4 ttl=64 time=1.30 ms

---

### Post by drdos2006 on 2010-05-18
Hmm.. Maybe make another user for the desktop ( it may be that you are trying to log in with the same user name on both machines and upsetting security ). Add the user name to both laptop and desktop Group settings.
Did you change smb.conf on both machines for the workgroup name ?
regards

---

### Post by Vi3GameHkr on 2010-05-19
As of now, I am currently upgrading the laptop to 10.04 32-bit.  I found out my desktop is on 64-bit, I thought that would be a good idea at the time.  Do you think there will ever be a time that 64-bit Ubuntu will be better?  Apparently less people use 64-bit and so it is maintained less?  Well either way, theoretically 64-bit should be better.  Anyways, I'll update this post when I can.

---

