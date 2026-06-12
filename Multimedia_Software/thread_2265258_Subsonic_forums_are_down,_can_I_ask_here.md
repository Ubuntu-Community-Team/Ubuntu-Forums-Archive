---
title: "Subsonic forums are down, can I ask here?"
date: 2015-02-13
forum: Multimedia Software
---

### Post by frankie5 on 2015-02-13
I'm a total newbie to anything Linux and I'm having some troubles with setting up the media folders in Subsonic and the Subsonic forums are down.
May I post my problem here in the Newbie section?

Thanks Frankie

---

### Post by Pumm4 on 2015-02-13
Hi** frankie5**, Welcome to the Forums!

By all means go for it, since Subsonic supports Debian and Fedora  ...
Do not worry, If you ask in the wrong section,your question will be either moved or merged (if you decide to post somewhere else).

Wish you the best!

---

### Post by Bucky Ball on 2015-02-13
*Thread moved to **Multimedia**.*

Welcome. You may have more luck here. 

> **Pumm4 said:**
> ... your question will be either moved or merged (if you decide to post somewhere else).

Please do not duplicate post your support request elsewhere on the forums. ;)

Which release and flavour of Ubuntu are you trying to do this on?

---

### Post by frankie5 on 2015-02-13
Thank you guys for the quick response.

Ubuntu 14.04 LTS
Subsonic 5.1

Problem : Media files are on an external Firewire drive (NTFS). Ubuntu sees the drive, I can copy, move, delete files, no problem. Subsonic runs, browser interface, but when I want to setup the media folders within Subsonic I get "Folder not found" message.

Ubuntu sees the device at /media/frankie/Media, to which I point Subsonic (/media/frankie/Media/Music/Flac).

fdisk shows the drive to be /dev/sda. It also says that the disk is GPT.

I really know nothing about Ubuntu/Linux (ex DOS and Windows guy).

---

### Post by coldraven on 2015-02-14
> fdisk shows the drive to be /dev/sda. It also says that the disk is GPT.
I'm not an expert but that looks like your main drive not the external one.
Try running ```
sudo blkid
```

The see here for mounting NTFS drives automatically at boot-up. Once you know the device's label or UUID you can edit /etc/fstab and add an entry there.
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

I don't know about Subsonic, it's probably just a permissions problem. That is, does the user "subsonic" have read permission on that drive?

---

### Post by frankie5 on 2015-02-14
blkid shows my external drive to be /dev/sdb2

I've modified fstab as per link provided buy adding this line to the end :
UUID=4E3A27E43A27C7B3 /media/frankie/Media ntfs-3g defaults,windows_names,locale=en_CA.utf8  0 0

I too, think it may be permissions. I've found the wiki for Subsonic permissions but I can't seem to follow the steps indicated.
[https://wiki.archlinux.org/index.php/Subsonic#Configure_permissions](https://wiki.archlinux.org/index.php/Subsonic#Configure_permissions)
P.S. Subsonic is installed in /var/subsonic  not in  /var/lib/subsonic

when in Terminal my promt looks like this : frankie@frankie-ubuntu:~$

---

### Post by frankie5 on 2015-02-14
I found this thread on installing Subsonic unrooted
[http://ubuntuforums.org/showthread.php?t=1658577&highlight=subsonic+forums](http://ubuntuforums.org/showthread.php?t=1658577&highlight=subsonic+forums)

So I uninstalled Subsonic to try the steps in the guide and I cannot even get the apt-get (for Tomcat6 and Lame) to work, error message about  "not open locked file", "no permissions", "unable to lock admin dir" and "are you root"

I'm extremely frustrated, wasted so much time getting nowhere, here I thought that Ubuntu was far enough advanced for "easy use" but it's making me rip out my hair, I'm seriously thinking of throwing out this machine and going back to WINDOWS, and now I have no more time until next weekend.

I'd be willing to give this one more shot, even to the point of reinstalling Ubuntu or even another flavour of Linux or another transcoding media server besides Subsonic. If someone could guide me to setup Linux without all this "permissions" crap with "locked", "unlocked" "root" stuff in would be highly apperciated. I'd even apperciate phone support, but these forums make everything slow like molassis. 

But it will have to wait until next weekend. 

Thanks for trying to help.

---

### Post by coldraven on 2015-02-15
Don't get too frustrated, any new system will have a learning curve. The reason that so many of us moved away from Windows was because it was so insecure.
I used to spend more time running virus, spyware etc. checkers that actually using it productively. 
There is a very good reason that Ubuntu does not just give you a root account. See the many posts on that subject from people who were used to the Windows way of thinking.
The only time I use a virus checker now is when I get media from a Windows user and can warn them that they have been hacked or prevent it from spreading to another Windows user.
Hopefully by next weekend the Subsonic forum will be back up and you can sort out your problems.

---

