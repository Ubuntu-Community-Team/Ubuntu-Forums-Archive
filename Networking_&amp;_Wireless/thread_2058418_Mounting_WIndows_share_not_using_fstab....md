---
title: "Mounting WIndows share not using fstab..."
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by inhumangeek on 2012-09-15
Hi I'm fairly new to mounting etc. 

I found this guide for mounting Windows shares in Ubunut, which works fine (allows me to write the the Windows folder OK):
[http://www.liberiangeek.net/2010/08/mount-windows-shares-ubuntu-10-04-lucid-lynx-terminal/]("http://www.liberiangeek.net/2010/08/mount-windows-shares-ubuntu-10-04-lucid-lynx-terminal/")

However I actually want to mount a share which is on a virtual machine which is hosted locally - so at the point that fstab is called, i.e. at boot, the share won't be available (as only after I log in does the VM load). So I want to run the mount command at some point after (Ubuntu) logon. (My VM starts automatically so I'd say 5 minutes after logon should be fine).

So there are two questions:
1) What is the command to run;
2) How can I run it 5 mins after logon. I have the gnome scheduler package which I think allows me to schedule tasks at a restart so perhaps this is a way forward?

For point 1), the following fstab line works:
```
//192.168.0.11/iTunes /home/paul/Windows cifs uid=paul,user=paul  0   0
```

I have tried running the following from the command line, this mounts the folder but doesn't allow me to write to the directory, presumably as I am not supplying my credentials:
```
sudo mount //192.168.0.11/iTunes /home/paul/Windows
```

I have tried running the full fstab line (i.e. with cifs,uid,user, etc) but this syntax doesn't work directly (presumably this is an obvious fact but I don't know enough!)... I am hoping there is some equivalent?

The other point is that to mount something using command-line mount I need to provide my superuser password - but I want this to happen automatically. If I could use fstab then this particular problem is avoided.

Many thanks for any advice.
Paul

---

### Post by Morbius1 on 2012-09-15
Just to be clear, If you are running VirtualBox and the host and guest are on the same system you don't need to use samba to connect to the share. If you create a VBox shared folder it will automatically mount the share at: **/media/sf_something**.

Anyway, to answer your question in general I would suggest Gigolo instead of fstab: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

What Gigolo will do when you set it up is run the following command every 60 seconds ( user adjustable ) until the share is mounted:
```
gvfs-mount smb://192.168.0.11/iTunes
```It automatically creates a mount point in your home directory here: **/home/paul/.gvfs/iTunes on 192.168.0.11**

It is in a hidden directory though so I would suggest creating a bookmark to /home/paul/.gvfs so Nautilus or any other application can access it easier.

---

### Post by inhumangeek on 2012-09-16
Brilliant thanks for the pointers I'll give them a go!
Point taken about VBox too.

Thanks,
Paul

---

### Post by inhumangeek on 2012-09-16
Morbius can you explain a bit further please? 

I know how to set up a shared folder in the host so that the guest can see it... but I want to do this the other way around. You said that such shared folders are automatically mounted at /media but how can I actually set up the share on the guest?

I have Ubuntu host and XP share, I want to share a specific folder within XP so that Ubuntu can see it...

Thanks.


UPDATE... actually scrub that it looks like you were assuming my host is Windows and my guest is Ubuntu. Done some searched and it doesn't look like what I want is possible so will have to try to get samba working.

---

