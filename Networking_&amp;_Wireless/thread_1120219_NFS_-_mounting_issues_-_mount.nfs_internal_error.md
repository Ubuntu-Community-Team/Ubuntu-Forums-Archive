---
title: "NFS - mounting issues - mount.nfs: internal error"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by dannyboy1121 on 2009-04-08
Hi Folks 

Recently upgraded from Gutsy to Hardy and then Intrepid (Server).

From Hardy onwards I've been unable to mount NFS exports from my NAS device. Nothing has changed on the NAS.

I've seen a lot of bug related posts for "mount.nfs: internal error" - mostly relating to Hardy and problems with nfs-common utils. This is what prompted me to upgrade to Intrepid. The problems are still present though. *cry*

Are there any known fixes for this issue - or should I just accept that the ability to mount NFS exports in the last two releases is bugged out?

Regards

---

### Post by Jose Catre-Vandis on 2009-04-08
No problems here with Hardy or Intrepid with regard to mounting nfs shares (not gloating, honest)

Have you installed portmap and nfs-common on your Ubuntu client?

Please detail your exports from your NAS and your mount lines (in fstab) or command lines to mount your nfs shares, to see if there is a syntax issue to be resolved.

---

### Post by dannyboy1121 on 2009-04-09
Here's the export:

+++++++++++
/media          192.168.1.0/255.255.255.0(rw,no_root_squash,async)
+++++++++++

portman and nfs-common are installed:

:~#dpkg -l | grep portmap
ii  portmap                               6.0-6ubuntu1                   RPC port mapper

:~# dpkg -l | grep nfs-common
ii  nfs-common                            1:1.1.2-4ubuntu1.1             NFS support files common to client and serve


mount command and results:

root@saturn:~# mount -t nfs neptune:/media /mnt/neptune/media
mount.nfs: internal error

****! If anyone has any advice - please pass it on.

---

### Post by Jose Catre-Vandis on 2009-04-09
Hmmm, having done some testing, I seem to have the same problem when trying to mount manually. However, mounting works fine from /etc/fstab. Try a line like this in your /etc/fstab file
```
sudo nano -w /etc/fstab
```
> neptune:/media /mnt/neptune/media nfs rsize=8192,wsize=8192,timeo=14,intr,bg

I would replace "neptune" with the IP of the NAS for testing purposes.

Then run this:
```
sudo mount -a
```
or
```
sudo mount /mnt/neptune/media
```

That should at least get you mounted. If you don't want to automount when you boot up, you can either disable nfs-common from autostart, and call it when needed, or write a small script to replace /etc/fstab with another /etc/fstab that contains the NAS share. Dirty but it would work.

Also, try out showmount just to ensure the NAS _is_ serving up :)
```
showmount -e neptune
```

{EDIT - NOTE} Just tried adding a new nfs share from a different box and the manual command worked fine, so there must be some "stuff" in a cache or mtab or the fact it is already in fstab that causes the command to not run.

---

### Post by dannyboy1121 on 2009-04-10
> **Jose Catre-Vandis said:**
> Hmmm, having done some testing, I seem to have the same problem when trying to mount manually. However, mounting works fine from /etc/fstab. Try a line like this in your /etc/fstab file
```
sudo nano -w /etc/fstab
```


I would replace "neptune" with the IP of the NAS for testing purposes.

Then run this:
```
sudo mount -a
```
or
```
sudo mount /mnt/neptune/media
```

That should at least get you mounted. If you don't want to automount when you boot up, you can either disable nfs-common from autostart, and call it when needed, or write a small script to replace /etc/fstab with another /etc/fstab that contains the NAS share. Dirty but it would work.

Also, try out showmount just to ensure the NAS _is_ serving up :)
```
showmount -e neptune
```

{EDIT - NOTE} Just tried adding a new nfs share from a different box and the manual command worked fine, so there must be some "stuff" in a cache or mtab or the fact it is already in fstab that causes the command to not run.

Hi Jose - thanks for all your help so far. I'm unable to try the 'mount -a' suggestion because the system is pxe booted with the root mounted via NFS. mount -a kills the connection to root.

I think the important thing to remember is that it was working until the upgrade with all the same exports from the NAS.

I've tried connecting from a RHEL5 server using the same commands and it connect first time no problem. This seems to suggest that the NAS (hacked NSLU2) is operational. exportfs shows the mount point being served up.

What's confusing is that the problem manifested in Hardy and upgrading to Intrepid hasn't cleared it. So if it is an issue with NFS it's been broken in multiple distro's (something I find hard to accept).

It appears that I'm not the only one here with these kinds of problems as a quick search reveals a number of nfs-common issues and bugs

I always wonder about advocating Ubuntu server use in a production environment - hell why not? Now I'm a bit less confident after encountering this issue. Imagine running and update and finding NFS is broken.

---

### Post by Jose Catre-Vandis on 2009-04-10
Hmmm, but was the RHEL server pxe booted with root mounted via NFS? ( You don't need to answer :)) Have you tried a straightforward Ubuntu client, as I have no problems connecting to a ubuntu server or a NAS. Is it possible there is something different goign on in your pxe boot environment that is blocking access?

---

### Post by lensman3 on 2009-04-10
Are ports 2049 open for both tcp and udp?  No firewall running?

Also check to make sure that your mount point is not the same place that "automount" is using.  The automount system somehow takes over its mount point, and nothing except it will allow a directory tree to be mounted.  Root can't override automount.  Something happens to the mount point deep in the kernel.  Automount uses the "autofs" moniker.

---

### Post by Jose Catre-Vandis on 2009-04-10
> **lensman3 said:**
> Are ports 2049 open for both tcp and udp?  No firewall running?

Also check to make sure that your mount point is not the same place that "automount" is using.  The automount system somehow takes over its mount point, and nothing except it will allow a directory tree to be mounted.  Root can't override automount.  Something happens to the mount point deep in the kernel.  Automount uses the "autofs" moniker.
[B]
Brilliant![/B] I tried manually mounting one of my nfs shares to a different mount point and it worked :)

For example:

Mounted by fstab:

NFS Share: 10.10.10.70:/media/music
to /home/music

only works with "sudo mount -a" or on boot

wheras if I unmount /home/music and then make a new directory, say "/home/mymusic" and run

```
sudo mount 10.10.10.70:/media/music /home/mymusic
```

it mounts up fine.

---

### Post by dannyboy1121 on 2009-04-11
No autofs here folks :)

More than likely I've screwed my latest kernel and ruined my nfs capabilities ... currently running 2.6.29

Time to make a new one.

I wish messing about with Linux wasn't so damn addictive.

---

### Post by dannyboy1121 on 2009-04-11
Just for the record in case someone else has the problem and comes across this thread during a search - 

I've fixed this. The issue was to do with the custom kernel I had compiled. I included the experimental options under NFS client and server which appeared to kill my ability to mount. 

Kernel recompiled without experimental options and it all works again.

Thanks for listening - you've been a great audience. :)

---

### Post by Jose Catre-Vandis on 2009-04-12
And thanks for telling us about the custom kernel with experimental NFS options in your first post!!! :twisted:

---

### Post by dannyboy1121 on 2009-04-12
Yeah sorry about that. I actually did the kernel upgrade a few days prior to the system upgrade but didn't pick up on the issue. Didn't think I had compiled in any different options than previous. Ooops.

---

### Post by Jose Catre-Vandis on 2009-04-13
I'm over it now :)

---

### Post by usererror on 2009-07-15
ok i know i am digging up an older post, but I ran into this same problem.

Background: I am setting up a mythtv front end with Mythbuntu. 

I duplicated my /etc/fstab nfs mount lines that my two other ubuntu desktops are using without any issues.

Situation: the difference between the three ubuntu workstations is that the 3rd one, the mythtv front end is using 8.10 instead of 9.04 due to video driver issues with ATI and my "legacy" video card.

I had all 8.10 stations a year ago and i could NOT for the life of me mount nfs shares to anything but /home/user/* paths. I was trying to mount my mythtv shares directly to /var/lib/mythtv/videos /music /pictures... and nfs would always fail at boot.

Resolution: mount the nfs shares via fstab to /home/user/xxxx and then create symlinks from the /var/lib/mythtv/xxx folders to the /home/user/xxx folders.

probably not conventional but it works, the only issue is i don't know WHY this works and my original method does not.

---

