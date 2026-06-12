---
title: "mp3 player does not auto mount, but I can manually mount it."
date: 2008-04-23
forum: Multimedia Software
---

### Post by Sh4wn on 2008-04-23
Hi,

I have a Sony Plug n Play mp3 player (so sonicstage isn't needed), and it worked always perfectly on Gutsy. recently I switched to Hardy RC2, but when I connect my mp3 player, it doesn't automatically mount.

After some research (sudo fdisk -l) I found out my mp3 player was connected, bit Gnome just didn't mount it. So when I manually mount it
```

sudo mount -t vfat /dev/sdf1 /media/WALKMAN

```

It just worked, although I can't edit anything, I can't add any files, I can't delete something. Howe can I fix this?

Thanks in advance

---

### Post by Sh4wn on 2008-04-23
Well, I found out, I can write and edit etc when I start nautilus under root, but it's still strange why my mp3 player doesn't automatically mount..

---

### Post by aparigraha on 2008-04-23
try modifying your fstab. back it up before you edit it.
[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by kennethmsmith on 2008-04-29
I also have a Sony Walman MP3 model NWZ-S615F.  It mounted in 7.10, although I recall having some issues with stability in transfering files.  Now with 8.04 it doesn't auto mount.  So I need to mod my fstab file I thought.. but then I saw the below info on another forum post.  Now I'm not sure what to do.  Anyone have a good step by step procedure for making these players mountable and writable for MP3s?

post I found:

automount of vfat memory devices can be affected by the upgrade to Hardy 8.04

Here is a solution:
Open Applications > System Tools > Configuration Editor

Go to the key system > storage > default_options > vfat
Edit the mount_options key by removing the usefree option.

You may need to reboot.
The devices should then automount when plugged in: i.e. the icon will appear on the desktop.

I emailed one of the developers involved, Martin Pitt.
Quote: 
 
That's indeed the right solution. 'usefree' is deprecated in Hardy (it
was only a temporary hack in Gutsy), and thus the gnome-mount
option 'usefree' has been removed in Hardy again.

You need it in Gutsy to avoid minute-long hangs when mounting a VFAT
drive. In Hardy this was fixed properly in the kernel.

---

### Post by Sh4wn on 2008-04-29
Hmm, I don't have an option usefree here..

---

### Post by kennethmsmith on 2008-05-01
yeah I noticed that too after checking it out myself... it appears that might be for a different distro.. not ubuntu.

I was able to mount my Sony Walkman (manually) using pmount

STEP 1: Acquiring the device ID

-------- To list your devices, first connect your USB device (it does not need to be mounted).  Then -------- type:

ls /dev/disk/by-label -lah


STEP 2: Mounting the Player

pmount /dev/<device ID> Walkman

------- &#8220;creates a directory in /media/ by the name of Walkman, and mounts the device there&#8221;

-------  Note:  To unmount use :

pumount Walkman

---

### Post by Sh4wn on 2008-05-01
AH great, that works better indeed :)

---

### Post by blakesmith on 2008-05-02
Ah yea!  Finally a working solution, many thanks man!

---

### Post by absolut1983 on 2008-05-11
Hi, folks.

   I'm having the same problem with my Walkman (which I didn't before upgrading to Hardy) and I'm not sure about what number to use as the device ID.

---

### Post by kennethmsmith on 2008-05-13
plug in your player.. open the terminal and type this:

ls /dev/disk/by-label -lah

Then post your results here.  We can help point it out to you.

---

### Post by absolut1983 on 2008-05-14
There you go, guys.

absolut@elh:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root  60 2008-05-14 10:32 .
drwxr-xr-x 6 root root 120 2008-05-14 10:32 ..
lrwxrwxrwx 1 root root  10 2008-05-14 10:32 WALKMAN -> ../../sdb1

   Cheers.

---

### Post by kennethmsmith on 2008-05-14
looks like the device id is "sdb1"

---

### Post by absolut1983 on 2008-05-15
It is, indeed.

   Thanks a million, man.

---

### Post by Rix Computer Engineer ~# on 2008-09-19
I have been following the instructions. However my system tells me my Sony Walkman is mounted but there is no icon on y desktop. Also when I navigate to the mounted directory and ls it shows nothing.

Any advise. I am using Kubuntu 8.04. on.

Here is my output.

veronique@delici:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x+ 2 root root  60 2008-09-18 22:07 .
drwxr-xr-x+ 6 root root 120 2008-09-18 22:07 ..
lrwxrwxrwx+ 1 root root  10 2008-09-18 22:07 WALKMAN -> ../../sdb1
veronique@delici:~$ pmount /dev/sdb1 WALKMAN
Warning: device /dev/sdb1 is already handled by /etc/fstab, supplied label is ignored
mount: only root can mount /dev/sdb1 on /mnt/sony
veronique@delici:~$ sudo pmount /dev/sdb1 WALKMAN
[sudo] password for veronique:
Warning: device /dev/sdb1 is already handled by /etc/fstab, supplied label is ignored
veronique@delici:~$ sudo pmount /dev/sdb1
mount: /dev/sdb1 already mounted or /mnt/sony busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt/sony
veronique@delici:~$

Any feedback would be awseome.

---

### Post by kc8hr on 2010-02-05
> **kennethmsmith said:**
> 
STEP 1: Acquiring the device ID

-------- To list your devices, first connect your USB device (it does not need to be mounted).  Then -------- type:

ls /dev/disk/by-label -lah

That didn't work for me, 'tail /var/messages' did, tho.
> 
STEP 2: Mounting the Player

pmount /dev/<device ID> Walkman

------- “creates a directory in /media/ by the name of Walkman, and mounts the device there”

-------  Note:  To unmount use :

pumount Walkman

Excellent solution, much better than 'sudo mount. . .' etc.

I have a camera and several thumb drives that automount, wonder why MP3 players won't? Some sort of collusion with the RIAA??? ;)

Thanks,
Tim

---

