---
title: "how to mount network drive automatically ONLY when present"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by ezm on 2011-06-10
Hi All,
I have a network drive connect to my lan with iomega's iconnect device.  I am getting tired of mounting the drive manually each time I want to use it.  I would like therefore to have it mounted automatically on boot by  placing a line in fstab, but since the computer (a laptop) won't always be connected to my home lan, this might cause problems.  Is there a way to list the drive in fstab so if the drive is not present it will just move on?

ezm

---

### Post by lesser on 2011-06-10
In my experience, network drives that are not available during boot, simply do not show up. The only noticeable thing will be an error line in dmesg.

---

### Post by Morbius1 on 2011-06-10
Gigolo !

That's not an accusation it's a utility: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

When implemented as described above it will on boot attempt to connect to and mount the remote share. If the remote share is not present at that time Gigolo will scan the network at user defined intervals in perpetuity until it is available and mount it.

I don't know how you are mounting it now but Gigolo depends upon gvfs-mount and as such it does have one irritating drawback - it's mount point is fixed and located in a hidden directory:
> /home/username/.gvfs/share-name on server-nameThe ususal remedy for this is to create a symlink to a non-hidden directory if any application has a problem with a hidden mount point. But if you using the remote share to drag and drop files from one location to another it doesn't matter where the mount point is located.

---

### Post by ezm on 2011-06-12
Morbious1, I may just try this Gigolo tool.  So far I've tried just adding a line to my fstab:


//192.168.1.5/NEW_YORK /media/NEW_YORK smbfs credentials=/etc/samba/cred-file

This works fine in terms of mounting on boot.  The boot process doesn't seem to lag at all when the drive is not present.  There's no error that the user sees.  

However, I am having a problem during shutdown or reboot.  Every time that I have not unmounted the drive before I shutdown the computer, the shutdown fails.  

Any ideas?

---

### Post by ezm on 2011-06-13
My one guess was that the shutdown process is closing the internet connection before it issues the unmount command, which then produces an error.  But I'm not sure how to confirm that hypothesis or what to do about it.

---

### Post by Morbius1 on 2011-06-13
> **ezm said:**
> However, I am having a problem during shutdown or reboot.  Every time that I have not unmounted the drive before I shutdown the computer, the shutdown fails.  

Any ideas?
Um ... Gigolo !

Seriously. Gigolo has an advantage not only in the beginning process but at the end as well. It works in user space so when you shut down the user is logged off first and with that all his mounted services. Only then does the shutdown process move on to the network connection and the rest of the mounted services in fstab.

---

### Post by ezm on 2011-06-13
> **Morbius1 said:**
> Um ... Gigolo !

Seriously. Gigolo has an advantage not only in the beginning process but at the end as well. It works in user space so when you shut down the user is logged off first and with that all his mounted services. Only then does the shutdown process move on to the network connection and the rest of the mounted services in fstab.

I installed it and tried it out.  It does work well.  I agree.  The main problem, which is just an annoyance, is that since the network is not present at first I have to wait the autoconnect interval (set to 60 by default) for the drive to be connected at the beginning.  I'm not sur if it is wise to set it for a shorter interval, say 10.  Might this jam up the system in the case that the network drive is not present?  

Re the fstab method.  I still think this is the neater solution as it doesn't require running a separate program.  Interestingly, the fstab method is good at waiting for the network drive to be present.  When I log onto ubuntu at first, the drive is not there, but as soon as the wlan connection is established the drive is mounted.  I don't quite get why it's not so smart the other way around... I'd still like to find a solution for the fstab method.  So if anyone has any ideas... 

ezm

---

### Post by rivode on 2011-06-13
Maybe "automount" will do what you want, have a look at the "autofs5" or "afuse" packages.  I haven't used it in years, but I think you put it in your fstab, and it will try to mount the share when you access the appropriate directory.

---

### Post by Morbius1 on 2011-06-13
I've never used autofs but based just on what I've read that does seem like a possible solution. Worst case it appears as though the mount disappears when not is use so it's likely it's not mounted anyway when you decide to shut down.

BTW, You might want to look here for other possible workarounds ( one of which is autofs ):
**Network is brought down before network filesystems are unmounted (CIFS timeout at shutdown): **[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211631](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211631)

It's only a 3 year old bug so I'm sure the permanent fix is just around the corner ;)

---

### Post by sd@ksu on 2012-05-23
Write a script and put it in rc.local

---

