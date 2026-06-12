---
title: "NTFS File Sharing &amp; owner changing"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by 484 on 2009-02-15
I run an Ubuntu XP dual boot. I wish to mark a folder in my NTFS file system as shared under Ubuntu, but the folder belongs to the root administrator. No problem, I logged in as root and verified that I could share the file. Then I attempted to change the owner of the folder to my usual account, The folder IMMEDIATELY switched its owner back to root. I get the same thing when I do this from the command line.

The folder is on a 20 GB IDE hard drive connected via a RAID card (I do not have a RAID array set up, I just use it for the extra IDE ports). Under windows the folder is located at:
F:\B-UP\My PIctures\Desktops
In Ubuntu it is
/media/sdc1/B-UP/My PIctures/Desktops

I would like to be able to share folders in my windows file system without having to stay logged in as root.

---

### Post by graysky on 2009-02-15
You're dual booting so you can only boot into Ubuntu when XP isn't booted at all, right?  In otherwords, we're only dealing with a single PC, right?  Windows sharing in this scenario has NOTHING to do with the task you're looking to accomplish since Ubuntu can read/write to any NTFS partition regardless of the windows permissions when windows isn't booted.

How are you logging into Ubuntu as root anyway?  You should be using sudo to do root stuff.

To mount an NTFS partition from Ubuntu make sure you have ntfs-3g installed:
```
$ sudo aptitude install ntfs-3g
```

Now add the following to your /etc/fstab like this:
```
$ sudo nano /etc/fstab
```

Add the following line:
```
/dev/sdc1 /media/DIR          ntfs-3g defaults        0       0
```

That will mount the entire partition to /media/DIR with rwx permissions to all your system users at boot - I dunno how you can selectively mount a directory under a partition though.

After you save the /etc/fstab you can either reboot or simply mount it manually by this command:
```
$ sudo mount /media/DIR
```

---

### Post by 484 on 2009-02-15
When I run sudo mount, I get

:/media$ mount /dev/sdc1
mount: according to mtab, /dev/sdc1 is mounted on /media/sda1
mount failed

---

### Post by 484 on 2009-02-15
I tried rebooting, and another harddrive was mounted to the /media/DIR with my regular user account as owner: moving in the right direction :D.

---

### Post by 484 on 2009-02-15
Here's what I did:
make folders in /media/ that my user account has ownership of for each partition
find name of the actual device (using gparted)
mount device to created folder

Thank you for your help

---

### Post by 484 on 2009-02-15
It appears I was mistaken, I still cannot change the ownership of files inside the drive, just of the drive itself.

---

### Post by nexus86 on 2009-02-15
Hi,

I have PC a running XP yay :/ and Ubuntu on laptop yay :D

I network these 2 boxes right, I want to access my NTFS partition on my UBUNTU box from my XP box via my local area network.

Can this be achieved?

Any help or advice will be much appreciated.

Thanks,

---

### Post by graysky on 2009-02-15
> **nexus86 said:**
> Hi,

I have PC a running XP yay :/ and Ubuntu on laptop yay :D

I network these 2 boxes right, I want to access my NTFS partition on my UBUNTU box from my XP box via my local area network.

Can this be achieved?

Any help or advice will be much appreciated.

Thanks,

What you're describing can be enabled via Samba and is format independent.  In other words, NTFS, ext3, XFS, etc. can all be shared via Samba.  There is a great howto on the topic in these forums.

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Since you only have 3 posts, I'm assuming this is all new to you.  The search feature is your best friend, well, google is your best friend, the search feature is a close second.  Even if you never heard the term 'samba' before, simply searching in google on these three words gave the answer in the first three hits: **share ntfs linux**.  I'm not flaming you, just [helping you learn to fish](http://www.amatecon.com/fish.html).

---

### Post by nexus86 on 2009-02-15
Funny grysky :)

I do search indeed, I don't make a habit of asking n00b questions.

I do use "The Google" and forum for searching, just tough searching if you don't know exactly what you are searching for.

One dude actually said NTFS write was too unstable etc etc and that using the NTFS part on your linux box via windows was not possible, so I thought I would ask it here :P

Thx for the URL.

---

