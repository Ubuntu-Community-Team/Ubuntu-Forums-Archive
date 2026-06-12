---
title: "Editing fstab for conditional nfs mounting"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by sd@ksu on 2012-02-24
I shall explain my situation below. I have set up a small network of 3 computers in our lab with ubuntu 11.04 (32 bit). I am using nfs for file sharing. The server is set up such that when the clients boot up, server's home will be mounted as the home of the clients also. For this I have added the following:

1) in server's /etc/exports:
```
/home clientIP(rw,sync,no_subtree_check)
```

2) then restarted the nfs kernel server.

3) Next is the contents of client's /etc/fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=a33e6c76-f42f-4953-b93c-172160321ab2 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c05b9b15-ebcf-4945-b08d-34fede0e4273 /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=04d92ef1-6118-4ca2-8cee-77a69f2363dd /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8c09ada0-0d3c-44ed-a036-e96c04b08502 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# mount point for localhome
UUID=04d92ef1-6118-4ca2-8cee-77a69f2363dd    /localhome    ext4    defaults    0    2

#nfs mount from server
server,sIP:/home    /home    nfs    nfsvers=3,_netdev,exec,dev,suid,rw    0       0

```
........................................

The idea is to mount the home folder from server for all the users (user identification is made by suid option and new users are created with same uis and gid on both the server and the clients). Also in case the server is down or nfs mounting fails, the client(s) will mount the local home. And that's where the problem comes and I am at a loss what to do. If server is online, things work fine. For all users, the home will mount from the server. Also I have tested that anything saved locally can be accessed from the localhome. But in case server is down and i am trying to boot the clients, the following happens:
1) The system will boot and the user login screen appears.
2) After you login to a user with user name and password, the desktop does not come. Instead the following error messages will appear one by one:
[IMG]https://lh6.googleusercontent.com/-TChHssysEDk/T0csuRxtUuI/AAAAAAAACkw/lgE-uEg59i4/w1054-h291-k/a.png[/IMG]

[IMG]https://lh6.googleusercontent.com/-a-bnVx2sBaA/T0csuV7Za-I/AAAAAAAACk4/YkeGuGmuFjU/w500-h162-k/b.png[/IMG]

[IMG]https://lh5.googleusercontent.com/-BR84gKlvNR0/T0csuVIcO0I/AAAAAAAACk8/Z3ARalHCGmM/w399-h212-k/c.png[/IMG]

.........................
And then the desktop is blank. I can not do anything!

Now I know why these are coming. Because of the condition in fstab, if server is offline, nfs mounting of home fails. As such there is no home directory for the user 'installer' and the .ICEauthority is not available. If I go to recovery mode and do sudo mount -a it tells me: [COLOR="Red"]"mount.nfs: No route to host"[/COLOR]. I was thinking is there a way to write a script or program the boot or add an option in fstab such that: 
Try mouning home from server (by nfs mount).
If home mounting from server (using nfs) fails, then mount the home folder from "UUID=04d92ef1-6118-4ca2-8cee-77a69f2363dd" which is mounted on the /home locally using the code below:
[CODE]
# /home was on /dev/sda7 during installation
UUID=04d92ef1-6118-4ca2-8cee-77a69f2363dd /home           ext4    defaults        0       2
[CODE]
 I hope I have been able to explain my problem. Please help me quickly, anyone. Thanks in advance.

---

### Post by roelforg on 2012-02-24
I'd do it like this:
```

#!/bin/bash

mount -t nfs server.local:/homeshare /home
if [ $! != 0 ]
then
  mount /<path_to_local_home_drive_or_partition> /home
fi


```

---

### Post by sd@ksu on 2012-02-24
@ roelforg:
Do yo want me to add these lines in my fstab ? Or a seperate script file ? Where do I keep that script file then so that it runs when the system boots ? I am relatively new in Linux, please pardon my ignorance.

---

### Post by roelforg on 2012-02-24
It's a bash script; make it run at boot right after the network has been started.
Info about running at boot should be on the wiki.

---

### Post by sd@ksu on 2012-02-24
Can you please guide me to that page ?

---

### Post by roelforg on 2012-02-25
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
This one is the easiest: [http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by sd@ksu on 2012-02-25
i have tried following the instructions in 2nd link (with defaults option) but it does not work..:(

---

### Post by roelforg on 2012-02-25
> **sd@ksu said:**
> i have tried following the instructions in 2nd link (with defaults option) but it does not work..:(
Yeah, haven't worked with autoboot stuff for a while...
Google ubuntu init script

---

### Post by sd@ksu on 2012-03-06
Got it solved...never mind...

---

### Post by Captain James T Kirk on 2012-04-25
Just wanted to point out how poor it is to come here and ask for advice and have one of the forums best help, then follow up with a "got it solved never mind".

Happens all too often yet the excellent minds here keep helping and having to help more often because of OP's such as this one who are too lazy to come back and help others by explaining what they did.

Very poor sd@ksu

But as always, good show roelforg :D

---

### Post by sd@ksu on 2012-06-01
@ Captain James T kirk: sorry mate for being lazy and not putting up a solution...actually the issue has evolved with time and the solution i had...off course by taking help from some other ubuntu forums... I have an unfinished help written for my problem and the solution and I shall post it soon. To be true, I was first going to shout back at you and then I realized that you are right. THanks for pointing it out. I shall surely post the help soon in a separate thread and post the link here.

---

### Post by JasperHorn on 2013-01-12
> **roelforg said:**
> I'd do it like this:
```

#!/bin/bash

mount -t nfs server.local:/homeshare /home
if [ $! != 0 ]
then
  mount /<path_to_local_home_drive_or_partition> /home
fi


```

For those ending up here in the future: that should be $? not $!

(I am mounting a disk on through different mean (ntfs/cifs) depending on whether the Ubuntu is running natively or under a VM (in which it has no access to the partition. I managed to get it to work with the information from this topic, thanks!)

---

