---
title: "how do i access my camera's mount point?"
date: 2008-06-01
forum: Multimedia Software
---

### Post by falcoM on 2008-06-01
so I am very new to Ubuntu, I love it but I am very new to it. I have had dual boot XP/Ubuntu and have been using it more and more.

Today I ran into a problem where I can't figure out how to access the directory of my camera's mount point. I plug in the camera it starts up...F-spot finds it and offers to import, does so successfully. BUT I can't figure out where to find the mount point to cd into it. gThumb has no problem with finding it via the file>import photos...

can anyone please help me?

---

### Post by tamoneya on 2008-06-01
it should be /media/something.  If you look around you should see something that looks like you camera.  I think my computer always does it to /media/CANON or something.  Since my camera is a canon SD1000 it made sense that /media/CANON is my SD card.

---

### Post by falcoM on 2008-06-01
hmm I looked in /media and /mnt, there was nothing there. Now there are dirs named camera but I created those in my "feeling in the dark" method of somehow getting it mounted to where I know it would be.

Not sure if this is because I dual boot and Ubuntu has access to the Windows partition but my /media has all the Windows directories in it. In addition, somehow the /media/camera directory has everything in it from /media...odd.

So yea..if anyone can help I'd be very grateful. This quest started for me with this message. "from the shell cd to your SD card's mount point"

---

### Post by sisco311 on 2008-06-01
Use the mount command to list mounted partitions:
```
mount
```

---

### Post by falcoM on 2008-06-01
Used mount and get the following:

/dev/sda2         on  /                                        type  ext3                   (rw,errors=remount-ro)
proc              on  /proc                                    type  proc                   (rw,noexec,nosuid,nodev)
/sys              on  /sys                                     type  sysfs                  (rw,noexec,nosuid,nodev)
varrun            on  /var/run                                 type  tmpfs                  (rw,noexec,nosuid,nodev,mode=0755)
varlock           on  /var/lock                                type  tmpfs                  (rw,noexec,nosuid,nodev,mode=1777)
udev              on  /dev                                     type  tmpfs                  (rw,mode=0755)
devshm            on  /dev/shm                                 type  tmpfs                  (rw)
devpts            on  /dev/pts                                 type  devpts                 (rw,gid=5,mode=620)
lrm               on  /lib/modules/2.6.24-17-generic/volatile  type  tmpfs                  (rw)
/dev/sda1         on  /media                                   type  fuseblk                (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs        on  /sys/kernel/security                     type  securityfs             (rw)
binfmt_misc       on  /proc/sys/fs/binfmt_misc                 type  binfmt_misc            (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon  on  /home/alex/.gvfs                         type  fuse.gvfs-fuse-daemon  (rw,nosuid,nodev,user=alex)
/dev/sda1         on  /media/camera                            type  fuseblk                (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
gvfs-fuse-daemon  on  /root/.gvfs                              type  fuse.gvfs-fuse-daemon  (rw,nosuid,nodev)

---

### Post by falcoM on 2008-06-01
Alrite, so since I can't find it where it's getting mounted automatically can I specify where it should mount to so then I can access it?

---

### Post by sisco311 on 2008-06-01
I think is mounted in /home/alex/.gvfs:
```
cd ~/.gvfs
ls
```

---

### Post by ubunteduser on 2008-09-03
This does not work. It is not behaving as in 6.04. Ubuntu make it fancy with the auto f-spot pop-up, and now the old true and tried automount does not work.

Where can I find the /dev? I can see that it is  usb 2-4 address 5. Now what device would that be?

[81281.303606] usb 2-4: new high speed USB device using ehci_hcd and address 5
[81281.437197] usb 2-4: configuration #1 chosen from 1 choice

---

### Post by ubunteduser on 2008-09-13
The developers screwed it up. They tried to make it fancier by auto launching f-spot. To do this the device is not mounted as a file system. Thus you can't use it conveniently like a filesystem anymore.

This is an example of developer getting it wrong. 

Anyways, to solve the problem, I bought  a USB media reader and put my card in there rather than plug the camera in directly. The card now gets mounted.

---

### Post by trash on 2008-09-13
> **ubunteduser said:**
> The developers screwed it up. They tried to make it fancier by auto launching f-spot. To do this the device is not mounted as a file system. Thus you can't use it conveniently like a filesystem anymore.

This is an example of developer getting it wrong. 

Anyways, to solve the problem, I bought  a USB media reader and put my card in there rather than plug the camera in directly. The card now gets mounted.

You could just go into preferences and change how it's handled when plugged in.. i'm in xubuntu and i forget what it is in gnome, but basically in removable media you give it a command like 'nautilus' and it should open no prob.. maybe!

---

### Post by bve on 2008-09-27
> **trash said:**
> You could just go into preferences and change how it's handled when plugged in.. i'm in xubuntu and i forget what it is in gnome, but basically in removable media you give it a command like 'nautilus' and it should open no prob.. maybe!

Actually Hardy still doesn't mount the camera, in fact if I disable the f-spot-import action from Control Center --> Removable Drives and Media --> Cameras tab and then set Control Center --> File Management Preferences --> Photos to 'Open Folder' nothing happens.

If I run  tail -f /var/log/messages before attaching the camera it shows it only detecting a usb device.

```

Sep 27 12:01:24 zeus kernel: [327178.064919] usb 1-8: new high speed USB device using ehci_hcd and address 3
Sep 27 12:01:24 zeus kernel: [327178.198765] usb 1-8: configuration #1 chosen from 1 choice

```

My camera, a new Fuji Finepix S1000fd (which is an awesome value for it's price btw) can do decent video, so I needed a way to mount it to get the .avi's off of it.

Both f-spot and gthumb could see the avi, however f-spot failed to import the avi's -- which doesn't surprise me since it is a photo db.

What I ended up doing was changing the command in Control Center --> Removable Drives and Media --> Cameras --> Digital Camera to 'gthumb --import-photos' without quotes. This at least allows me to get the avi files onto my pc, furthermore it returns my ability to delete the images from the camera as I import them.

---

### Post by veloce on 2008-11-17
I've found that the files are in ~/.gvfs/ and Nautilus finds them as gphoto2://[usb:005,004]/

That would be fine (elegant even) if I just want the files.  However, I want access to the device to attempt recovery of some deleted pictures using photorec.

Anyone know how to find the address of the device?

---

### Post by lcodeghini on 2013-01-03
Hope this helps -

Using Ubuntu 12.10, I'm able to access my camera on the command line using /run/user/<username>/gvfs/gphoto2:host=%5Busb%3A002%2C008%5D/

---

### Post by overdrank on 2013-01-03
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

