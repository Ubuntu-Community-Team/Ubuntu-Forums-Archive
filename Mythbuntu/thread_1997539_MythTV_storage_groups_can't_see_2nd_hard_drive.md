---
title: "MythTV storage groups can't see 2nd hard drive"
date: 2012-06-05
forum: Mythbuntu
---

### Post by JCboy on 2012-06-05
Hi,

I have stumbled upon either a mythtv-ubuntu bug or evidence I'm still a noob :-) , I'm not sure.  Either way, I cannot go any further without asking for your help as I have spent weeks trying to figure this out, troubleshooting and searching for similar problems posted on the forums, with no success so far.

What I am trying to achieve is having mythtv directories in a second hard drive, separate from the one with the operative system. The problem is that when I try to change the default storage group that comes with the installation for one subfolder in my 2nd HD, mythTV can't write to it.

Here is my setup:
Ubuntu 11.10 system with 2 internal 1Tb HD with several partitions.
Mythtv (single backend/frontend) installed from repository ppa:mythbuntu/0.25, using this command: 
    sudo apt-get install mythtv.
A partition in my second drive mounted to the filesystem at /content.  It is what I would considered properly mounted, as shown here from the fstab file:
   # <UUID>  <mount point>  <type>  <options>  <dump>  <pass>
   UUID=23af0479-7f92-4691-a3fc-5ebbc1ba888f /content        ext4    defaults        0       2

The UUID refers to a logical partition in my b drive, sdb6, as shown here:
   @:  blkid -U 23af0479-7f92-4691-a3fc-5ebbc1ba888f
   /dev/sdb6

In /content, I have created a subfolder named "mythmedia" and set up permission for MythTV to access it, as shown here:
   @:  /content$ ls -l | grep mythmedia
   drwxrwxr-x  2 mythtv mythtv        4096 2012-06-04 17:19 mythmedia

MythTV would work fine when using the default storage group "/var/lib/mythtv/recordings/".  However, when I attempt to change it from the backend setup to "/content/mythmedia/" nothing gets recorded.  The directory /content and all its sub-folders work fine for all other purposes (Nautilus, Samba, etc.), but for some reason MythTV doesn't want to use it (i.e. no Tuner would record to it).

It is also odd that when I exit out of the backend setup, it doesn't give me the message about the directory not existing, so presumably, the backend is able to see the folder is there.  However, when accessing the information at (breadcrumbs) MythTV frontend> Information Center > System Status> Machine status >, it shows only the space available in my main hard drive (the one with /boot, /, /home and swap), ignoring the larger drive mounted at /content.

Any assistance would be greatly appreciated.

---

### Post by tgm4883 on 2012-06-05
> **JCboy said:**
> Hi,

I have stumbled upon either a mythtv-ubuntu bug or evidence I'm still a noob :-) , I'm not sure.  Either way, I cannot go any further without asking for your help as I have spent weeks trying to figure this out, troubleshooting and searching for similar problems posted on the forums, with no success so far.

What I am trying to achieve is having mythtv directories in a second hard drive, separate from the one with the operative system. The problem is that when I try to change the default storage group that comes with the installation for one subfolder in my 2nd HD, mythTV can't write to it.

Here is my setup:
Ubuntu 11.10 system with 2 internal 1Tb HD with several partitions.
Mythtv (single backend/frontend) installed from repository ppa:mythbuntu/0.25, using this command: 
    sudo apt-get install mythtv.
A partition in my second drive mounted to the filesystem at /content.  It is what I would considered properly mounted, as shown here from the fstab file:
   # <UUID>  <mount point>  <type>  <options>  <dump>  <pass>
   UUID=23af0479-7f92-4691-a3fc-5ebbc1ba888f /content        ext4    defaults        0       2

The UUID refers to a logical partition in my b drive, sdb6, as shown here:
   @:  blkid -U 23af0479-7f92-4691-a3fc-5ebbc1ba888f
   /dev/sdb6

In /content, I have created a subfolder named "mythmedia" and set up permission for MythTV to access it, as shown here:
   @:  /content$ ls -l | grep mythmedia
   drwxrwxr-x  2 mythtv mythtv        4096 2012-06-04 17:19 mythmedia

MythTV would work fine when using the default storage group "/var/lib/mythtv/recordings/".  However, when I attempt to change it from the backend setup to "/content/mythmedia/" nothing gets recorded.  The directory /content and all its sub-folders work fine for all other purposes (Nautilus, Samba, etc.), but for some reason MythTV doesn't want to use it (i.e. no Tuner would record to it).

It is also odd that when I exit out of the backend setup, it doesn't give me the message about the directory not existing, so presumably, the backend is able to see the folder is there.  However, when accessing the information at (breadcrumbs) MythTV frontend> Information Center > System Status> Machine status >, it shows only the space available in my main hard drive (the one with /boot, /, /home and swap), ignoring the larger drive mounted at /content.

Any assistance would be greatly appreciated.

What permissions are set on /content

---

### Post by JCboy on 2012-06-05
> **tgm4883 said:**
> What permissions are set on /content

Thanks for your reply.  You are spot on.  The permissions for /content (as opposed to the sub-folder) didn't include mythtv as user nor group.  I've changed this and now it is working! Thanks.

Now I understand.  It seems MythTV developers expected me to give them the whole partition for exclusive MythTV use.  If I may say so, this aspect is not very well documented, really.  I know I can still put other stuff there. However, I don't feel comfortable giving permission to mythtv to access my other content. I know there are parameters for making sure some space is always left unused; and chances are the software will behave well and all, but it just feels wrong.  I will have to rethink my partition strategy accordingly.  Thanks for the enlightenment.

---

### Post by nickrout on 2012-06-05
you don't need to give myth permission to write to the rest of the drive, you can give your other directories in /content other permissions.

---

### Post by Kr0nZ on 2012-06-05
on my box, I have my home partition mounted to '/home' mythtv writes recordings to '/home/mythtv/recordings'
'/home' is owned by root
'/home/mythtv' and '/home/mythtv/recordings' is owned by mythtv

so maybe the folder containing the folder where myth writes recordings to needs to be owned by mythtv?

---

### Post by JCboy on 2012-06-07
It turned out that all I needed to do was just assign execute permission to the "o" class for the mount point directory for that drive (/content).  So actually I am able to leave ownership as I had it originally (no mythtv as user nor group), but with the execute bit on for "o".  This allows MythTV to traverse (cd) that directory and get to the one defined in storage groups Default (in my case: /content/mythmedia).

Now I am able to have mythtv directories in a second hard drive (separate from the one with the operative system), and neat permissions set so I can have the 2nd HD also used for some other stuff.

Thanks <nickrout>, <Kr0nZ> and again <tgm4883> and those from <mythtv-users@mythtv.org> as well.  It's been a great help.

---

### Post by anonymousdog on 2012-06-07
> **JCboy said:**
> It turned out that all I needed to do was just assign execute permission to the "o" class for the mount point directory for that drive (/content).
FWIW, when applied to directories, the execute bit allows traversal and that's all, no read access.  It is so commonly applied to directories even for the "other" class that the only common example of it's NOT being applied is the /root directory (root's home dir).

Also, even if you had had to apply mythtv group ownership to /content, sub-directories could easily have (group or user) ownership assigned to other groups or users.

---

### Post by JCboy on 2012-06-08
> **anonymousdog said:**
> FWIW, when applied to directories, the execute bit allows traversal and that's all, no read access. It is so commonly applied to directories even for the "other" class that the only common example of it's NOT being applied is the /root directory (root's home dir).
 
Also, even if you had had to apply mythtv group ownership to /content, sub-directories could easily have (group or user) ownership assigned to other groups or users.
Thanks.  This is useful because I don't know what common practice is, as I am learning this stuff just now.  What I go by (and normally works) is what make sense to me.  At first, I thought that giving "other" any kind of permission was a security risk.  Also felt that giving ownership (or even group) to mythtv at the top-most level (at least with respect to that hard drive) directory (/content, in my case) was not the right thing to do neither, kind of like it was beyond its jurisdiction.  I thought of this idea of creating a new group for the sole purpose of /content ownership and making mythtv part of that group, but was too cumbersome.  Balancing the first two, I opted for the o+x route which seemed neater.  I am glad to learn that other people would have done the same which means I am in the right track. Cheers.

---

### Post by nickrout on 2012-06-08
It's basic unix file* permissions, and there is some documentation out there that will suit you, I guess I learned linux when it was fairly "new" and most guides included this sort of basic level info.

Even still I get confused about directory ownership and permissions. Nice to know though that even / has execute permissions to the world. Try ```
ls -ld /
```

* everything is a file, including a directory. main exception: a network device, eg eth0. Not sure why that exception is so.

---

### Post by JCboy on 2012-06-11
> **nickrout said:**
> It's basic unix file* permissions, and there is some documentation out there that will suit you, I guess I learned linux when it was fairly "new" and most guides included this sort of basic level info.
 
Even still I get confused about directory ownership and permissions. Nice to know though that even / has execute permissions to the world. Try ```
ls -ld /
```
 
* everything is a file, including a directory. main exception: a network device, eg eth0. Not sure why that exception is so.
 
Reassuring indeed.  Thanks, nickrout.

---

