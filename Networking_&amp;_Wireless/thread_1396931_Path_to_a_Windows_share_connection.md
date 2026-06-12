---
title: "Path to a Windows share connection"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by CTBuckweed on 2010-02-02
From the command shell, how do I get to a network connected drive?

I do a "Connect to Server" -> "Windows share" and connect to one of my Windows XP systems. Everything is fine. But how do I get to that drive from the command line prompt so I can do terminal commands or open files  programmatically (hmmm is that spelled right?) Thus far, I see no way to do it.

---

### Post by johnson.d on 2010-02-03
For temporarily mounting the network share

1) type the following command
$ mount //<ip address>/share /<mount point> -o user=<username>
2)Enter password

You can make it permanent by adding the following line '/etc/fstab' file

//<ip-address>/<share> /<mount-point> cifs user=<username>,password=<password> 0 0

---

### Post by dmizer on 2010-02-03
You'll need to mount the share. You can do this either via CIFS as outlined in the 2nd link in my sig, or you can try this: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by Morbius1 on 2010-02-03
When you use connect to server to access the remote share, nautilus creates a mount point. The problem is that because of debauchery and heavy drinking by the developers they put the mount point in a "hidden directory" It's in the ".gvfs" directory in your home folder.

To view it for yourself you have to enable nautilus to view hidden files:

[B]Nautilus > Edit > Preferences > Views > check "show hidden and backup files"
[/B]
So if you wanted to view the contents of the the remote share in a terminal you would have to do something like this:

Let's assume your username is john and the name of the remote share is winj and it's on a box named winxp:

Open Terminal
Type ls -al /home/john/.gvfs/"winj on winxp"

Yep, they made it worse by creating a mount point with spaces in it so you have to wrap " " around it.

Your alternative to this is to create a permantent mount point to a real ( non - hidden ) directory as suggested by dmizer above. Or you could create a symbolic link from the .gvfs mount point to a real directory - hopefully , one without spaces ;)

---

### Post by KeLa on 2010-02-03
I have made a symbolic link Network in my home directory pointing to .gvfs
and with that its very easy to access those mapped network drives from terminal.

I think this is the best way to solve it.

---

### Post by CTBuckweed on 2010-02-04
I wish to thank all you guys so much. With your help, I can now do what I wish through applications and the bash shell to get to my ntfs partitions on my other Windows systems at my home.

:KSThanks so much.:p

---

