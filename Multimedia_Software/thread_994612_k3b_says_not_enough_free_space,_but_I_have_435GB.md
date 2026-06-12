---
title: "k3b says not enough free space, but I have 435GB"
date: 2008-11-26
forum: Multimedia Software
---

### Post by BetterSense on 2008-11-26
It's very strange, I usually rip dvds to my home directory by using k3b's Copy DVD function with 'only make image' checked so it doesn't prompt me to burn. This has worked fine in the past, but now it complains that there is not enough free space in the temporary directory, while df says there is 400GB there. The amount of reported free space also changes all the time. If I try over and over sometimes it will be like 15gb, but then when I try it says > Unable to determine free space in temporary directory '/home/chaz/videos/dvds'

wtf mate?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=94335&d=1227758261[/IMG]

---

### Post by BetterSense on 2008-11-26
OMG I just tried it again and it said I had 1.9TB of free space! I only have a 1Tb HDD lol. Then it failed with the same 'Unable to determine free space' error.

---

### Post by cariboo on 2008-11-26
According to your screen shot you only have 448Mb of free spce in /tmp and your project size is .7Gb which to me means you're about 348Mb short of free space.

To clean up your hard drive and free up some space in a Applications--Accessories-->Terminal type:

```
sudo apt-get clean
```

and

```
sudo apt-get autoremove
```

Jim

---

### Post by BetterSense on 2008-11-27
I already did both of those commands. Besides, there is over four hundred gigabytes of free space in ~/videos/dvds, which k3b says it's using as my temporary directory. K3b is reporting nonsense numbers for available free space (sometimes even more than my hdd capacity), and then failing on an error of being unable to detect the free space. I use k3b like this constantly and it has always worked fine, it just started this. What could have changed with my system to start this? I just did an apt-get upgrade.

---

### Post by BetterSense on 2008-11-28
I uninstalled k3b and removed the k3b config in .kde. It still exhibits the same bug of reporting random amounts of free space every time and then, even when it reports enough, failing with the error of being unable to determine free space in /home/chaz/dvds/.

Where can I file a bug report, and, can anyone recommend an application that can rip dvd ISO files? Even a command line one, since that's practically all I use k3b for. Does dd work?

---

### Post by albandy on 2008-11-28
Open a console type df -lH and paste it here.

---

### Post by BetterSense on 2008-11-28
```
chaz@brutus:~/.kde/share/apps$ df -lH
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              9.9G   4.3G   5.1G  46% /
varrun                 1.8G   173k   1.8G   1% /var/run
varlock                1.8G      0   1.8G   0% /var/lock
udev                   1.8G    58k   1.8G   1% /dev
devshm                 1.8G      0   1.8G   0% /dev/shm
lrm                    1.8G    40M   1.7G   3% /lib/modules/2.6.24-12-generic/volatile
/dev/sda2              991G   501G   490G  51% /home
/dev/sdb1              3.9G   2.8G   1.1G  73% /media/JBWELD
/home/chaz/video/dvds/childrenofmen.iso
                       8.2G   8.2G      0 100% /home/chaz/mnt
chaz@brutus:~/.kde/share/apps$ 
```

what is with the /home/chaz/video/dvds/childrenofmen.iso line? I mounted childrenofmen.iso to /home/chaz/mnt, is there some ramifications to that?

Remember, I have k3b use /home/chaz/video/dvds as my temporary directory for the dvd image. Also k3b has reported up to 1.9TB of space as the 'Free space in temporary directory' line below the file path window in the screenshot above, which says 400some megabytes. The number is different every time.

I unmounted /home/chaz/mnt, which had /home/chaz/video/dvds/childrenofmen.iso mounted on it. Clearly this probably  the problem, although I haven't tried k3b yet cause I'm using acidrip right from the disc right now. 


```
chaz@brutus:~$ sudo umount mnt
[sudo] password for chaz:
chaz@brutus:~$ df -lh
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  4.0G  4.8G  46% /
varrun                1.7G  168K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   56K  1.7G   1% /dev
devshm                1.7G     0  1.7G   0% /dev/shm
lrm                   1.7G   38M  1.6G   3% /lib/modules/2.6.24-12-generic/volatile
/dev/sda2             923G  467G  456G  51% /home
/dev/sdb1             3.6G  2.6G  998M  73% /media/JBWELD
```

---

### Post by albandy on 2008-11-28
create a folder in your home directory called tmp
then, change your k3b temp folder to /home/your_user_name/tmp

---

### Post by BetterSense on 2008-11-28
ok. Then everytime I have to move the dvd iso from ~/tmp to ~/videos/dvds, which I can do, but what does using the tmp folder accomplish?


k3b now works using the tmp folder, but ripping a dvd directly to ~/video/dvds fails in the same manner.

---

### Post by albandy on 2008-11-28
The /tmp folder is the system temp folder and usually it should work correctly, but you have 2 partitions.

The first one /dev/sda1 is mounted on / where /tmp is to and its only 10GB
the second one /dev/sda2 is mounted on /home  and has 900GB

So you've not enought free space in /tmp to do the DVD copy, is for this reason that I told you to change the k3b temp folder from /tmp to /home/your_user/tmp

---

### Post by albandy on 2008-11-28
The /tmp folder is the system temp folder and usually it should work correctly, but you have 2 partitions.

The first one /dev/sda1 is mounted on / where /tmp is to and its only 10GB
the second one /dev/sda2 is mounted on /home  and has 900GB

So you've not enought free space in /tmp to do the DVD copy, is for this reason that I told you to change the k3b temp folder from /tmp to /home/your_user/tmp

---

### Post by BetterSense on 2008-11-28
> So you've not enought free space in /tmp to do the DVD copy, is for this reason that I told you to change the k3b temp folder from /tmp to /home/your_user/tmp

But that's not what I did. The temp folder wasn't /tmp before. It was ~/videos/dvds, so that the dvd image appeared straight to my dvd directory. 

Creating and using a ~/tmp folder works, as does using ~/Documents and ~/music. It begins ripping right away. But using ~/videos/dvds doesn't work, and fails with the 'unable to determine free space' error.

At this point, I will simply rip dvds to my music directory, or to any directory I create, and copy it to my dvd directory afterwords. But I would really like to know why it's doing this.

---

### Post by albandy on 2008-11-29
I don't know what is happenning, maybe some problem with file permisions, try this:

sudo chown -R youruser /home/youruser/videos
sudo chmod 755 /home/youruser/videos/*  /*this assign execution perms to all files in videos folder */

or try renaming the folder and creating it again, only to see what happens.

---

### Post by Francewhoa on 2009-07-23
Same here. **I posted a solution at [http://ubuntuforums.org/showthread.php?p=7667989#post7667989](http://ubuntuforums.org/showthread.php?p=7667989#post7667989)**

---

