---
title: "Automount network drives using NFS"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by DeMus on 2012-03-13
Hi,
I have 2 computers, a desktop and a laptop, both running Kubuntu 11.10. What I am looking for is a really detailed setup for a network connection between those 2 computers using automount and NFS.
I have done it before using just NFS and as soon as one of the computers shuts down, the other one hangs because the network connection is still open. This happens btw both in samba and NFS, but only in the KDE version. With Gnome I never saw this.
Please somebody, explain to me in detail (and I really mean detail) how I can setup this connection so I won't have a hanging computer again.

Some details which you might use when writing the explanation:

shared drives on both computers: /home/DeMus
mount point on both computers: /home/DeMus/shares/ext-homedrive
external drives should be read-write accessible without passwords, guest access is fine with me

Please explain which packages I have to install on a clean Kubuntu setup, which files I have to add/change, etc, etc.

I know I ask much but I am so fed up with the issue I have. I love KDE, I really do, but I can't get these connections the way I want them. I have found several how to's on the net but somehow these don't work for me.
I will be forever in your debt when you can help me to fix this problem.
Thank you so much.

DeMus

---

### Post by DeMus on 2012-03-15
114 readers and not one answer. Come on help me please. I can't be the only one having this problem. How do you have your network organized, how does it work?

---

### Post by DeMus on 2012-03-16
One more time: Can somebody please write an extensive how-to about the combination of autofs and nfs on Kubuntu 11.10? And I really mean a detailed explanation inwhich every step is described, every install, every text file which needs to be changed, everything. Please. Please help me. This is driving me crazy.

---

### Post by drdos2006 on 2012-03-16
I just found your post. Here is something I started with.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)

regards

---

### Post by DeMus on 2012-03-16
> **drdos2006 said:**
> I just found your post. Here is something I started with.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)

regards

Thank you for your answer. This is one of the websites I visited also and it doesn't work. The how-to is written in 2006 and since then things have changed: portmap is no longer available.
I still can't find the right combination between an NFS how-to and an autofs how-to.
When I use nfs and mount drives using fstab, it works. But when I switch off one of the computers, the other one hangs completely.
So I do want to mount using autofs, which shuts down the connection after a certain time. Result: no hanging computers.
What I need is a complete and very detailed way of doing this, but nobody wants or can give me that.

---

### Post by drdos2006 on 2012-03-16
Try installing nfs-kernel-server and nfs-common on both machines ffrom a terminal, with:

sudo apt-get install nfs-kernel-server  nfs-common

then 
sudo mkdir /media/main_shared01  on the main machine 
and : 
sudo mkdir /media/slave_shared01  on the slave machine.

On your main machine.
From a terminal, use gedit to create a bash file with :

gedit /home/<my_computer_login_name>/Documents/mount_slave.sh
Type in :  
#!/bin/bash
sudo    mount    <IP_address_of_slave_machine>:/media/slave_shared01

On your slave machine.
From a terminal, use gedit to create a bash file with :

gedit /home/<my_computer_login_name>/Documents/mount_main.sh
Type in :  
#!/bin/bash
sudo    mount    <IP_address_of_slave_machine>:/media/main_shared01

Then on main machine, from the terminal type :
bash  /home/<my_computer_login_name>/Documents/mount_slave.sh
to mount the slave shared drive.

Then on slave machine, from the terminal type :
bash  /home/<my_computer_login_name>/Documents/mount_main.sh
to mount the main shared drive.
From each machine, copy over a test file, can be a text file.

If all that works OK, then we shall  proceed further.

regards

---

### Post by DeMus on 2012-03-17
drdos2006, thank you for helping me, I really appreciate it.
I have done what you wrote but it doesn't work.

The moment I start the script on the main PC I get an error saying:
mount: can't find 192.168.1.22:/media/slave_shared01 in /etc/fstab or /etc/mtab

When I follow your explanation I am not sharing a folder at all, just trying to mount one. This is why mount can't find anything, isn't it?

I would think I have to share a folder first. Do I use the file exports for that?

I hope you will continue helping me, I really want this to work so I can use my computers again like I have always done when I still used Gnome. Don't understand why KDE is so much different here.

Thanks.

---

### Post by drdos2006 on 2012-03-17
Yes, the next thing we have to do is set up the /etc/exports file.

For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255 the text is :

/media/slave_shared01 (with a space here)      192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)
on the slave machine and

/media/main_shared01  ( with a space here)    192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)
on the main machine.

Edit each machine from the terminal with: sudo gedit /etc/exports

Save each file and then restart the daemon with : sudo /etc/init.d/nfs-kernel-server restart. 

Then try mounting again.

regards

---

### Post by DeMus on 2012-03-18
I know I keep bugging you but it still does not work. I did every step you wrote, using ctrl-c and ctrl-v not to make typo's and I still get:

mount: can't find 192.168.1.21:/media/main_shared01 in /etc/fstab or /etc/mtab
on the slave computer and

mount: can't find 192.168.1.22:/media/slave_shared01 in /etc/fstab or /etc/mtab
on the main one.

One other thing I do would like to say is, I would like to use automount with a timeout so when I don't use the share anymore, it will be automatically unmounted and I don't end up with a hanging computer. A hanging computer is what I had with a mount using a line in fstab.

In the mount script it says to mount the shared folder in the other computer, but ti does not say where to mount it:
sudo mount <IP_address_of_slave_machine>:/media/slave_shared01
(where I did replace IP_address with the real numbers of course)

Is this correct, or do we need to change something?

Thanks again.

---

### Post by drdos2006 on 2012-03-18
Hi there.
No, you are not bugging me. The concept of Ubuntu is to help each other to improve our knowledge of linux and make using linux a more rewarding experience for each other.

For the moment remove the line in /etc/fstab where it is trying to mount 192.168.1.21 to test if the operation is able to mount the shared drives manually, then we will have a look at automatic operation.

From a terminal on the main type : bash  /home/<my_user_name>/Documents/mount_slave.sh  and
on the slave machine type : bash  /home/<my_user_name>/Documents/mount_main.sh

See if allows a connection both ways.

regards

---

### Post by DeMus on 2012-03-20
I have deleted the lines from the fstab file and now I can't mount anything. It looks like only those folder/drives which are mentioned in the fstab file will be mounted.

What am I doing wrong?

At the moment I have the situation like explained on this website:
[http://mostlylinux.wordpress.com/network/nfshowto/]("http://mostlylinux.wordpress.com/network/nfshowto/")
I made scripts to mount and to unmount the folders/drives and this works, although still not automatically.

Any ideas how to mount a drive using exports, nfs-common and nfs-kernel-server without fstab?

Thanks.

---

### Post by drdos2006 on 2012-03-20
OK, sounds like you have a connection between each machine which is what we wanted. 

The next problem is that if one machine starts up before the other, then the first machine to start up will never be able to automatically connect to the second machine, but the second machine will be able to connect automatically to the first machine.

I have not set up my home network to automatically connect so at this stage I would say you will need to run a cron job to run the bash scripts you have at a regular interval.

Your /etc/crontab file will look like this:
```

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

```

The first line is for minute, hour, day-of-month, month, day-of-week, user, and command.
you could edit /etc/crontab on your main machine and add something like this.

17 * * * * root  bash /home/my-user-name/mount_slave.sh

which would run the script every hour at 17 mins past the hour and on your slave machine :

20 * * * * root  bash /home/my-user-name/mount_main.sh

which would run the script every hour at 20 mins past the hour on your slave machine.

If you want to run the script every 20 minutes then 
00 * * * * root  bash /home/my-user-name/mount_slave.sh
20 * * * * root  bash /home/my-user-name/mount_slave.sh
40 * * * * root  bash /home/my-user-name/mount_slave.sh

might be an option. If anybody has a better way, then please make a comment.

regards

---

### Post by DeMus on 2012-03-23
And there was light.
Finally I have things working. This is how I did it:
On the website ```
[NFS HOW TO]("http://mostlylinux.wordpress.com/network/nfshowto/")
```I got all the info I need to setup an NFS connection between my 2 computers.
Then I wanted the autofs to kick in.

Install the autofs package, which is in the standard repositories of (K)ubuntu and LinuxMint.
Then edit the file: /etc/auto.master
Here you can setup the base mount point, write down the file name of the file where the details about the mount are placed and I used the time-out function. Auto.master for me looks like this:
```
/-  /etc/auto.home --timeout=5
/-  /etc/auto.video --timeout=5
```
This means:
/- tells that the basepoint for the shares is the root directory
Further details about a share can be found in the files mentioned and both shares use a timeout of 5 sec. This means after 5 sec of in-activity the connections is automatically unmounted. Yeah!

/etc/home looks like this:
```
/mnt/LinuxDesktopHome -rw,soft,intr 192.168.1.21:/home/<username>
```

/mnt/LinuxDesktopHome = the mount point I chose
-rw,soft,intr are the options I use
<ip-address>:/home/<username> is the shared home directory on the computer with the mentioned ip-address.

The file /etc/auto.video looks almost the same only the mount point and the shared folder name are different.
Use filenames like auto.xxxx for the maps files.

When the files have been created it is just the matter of reloading the new data in the autofs service:
```
sudo service autofs reload
```
and restart the service
```
sudo service autofs restart
```

Now I can just switch off one computer and continue to work on the other without having to reboot it first.

Thanks for all who contributed in this thread.

---

