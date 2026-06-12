---
title: "Disk Usage Analzyer Error?"
date: 2010-06-24
forum: Mythbuntu
---

### Post by jodajen2 on 2010-06-24
I just did a new install with Ubuntu 10.04, then add Mythbuntu.  I have 80g hd internal. I have a 20g / partition, 55g /home, 5g swap.  I also added a 1Tb external usb drive.  I had trouble with the permission on the 1Tb drive because it was NTFS.  I reformatted it to ext3 and was able to fix the permissions so myth could read and write.  

I have all the myth storage locations set to this external drive because there is so much space.  I have started to get some shows recorded and now have 30-40gigs of video.  
Disk Usage Analyzer start to give me warnings about space.  I double checked to comfirm that myth was writing to the external and it was.  I even removed 16gb from the /home directory and it still shows 100% usage even though it also says that there is 900+GB of free space.  

It is like Disk Usage Analyzer doesn't count the disk space on the external it even though it know is it there.  It is counting the data on the external against the 55gb on the /home.  

I have the external drive mounted to /media in the /home directory could it be part of the problem?

I searched the forum for problems like this but it seems like most people are out of space and need to clear it out.  I have plenty of space and it doesn't think so.

Any help would be greatly appreciated.

---

### Post by mikewhatever on 2010-06-24
What's the output of **df -h**?

---

### Post by jodajen2 on 2010-06-24
> **mikewhatever said:**
> What's the output of **df -h**?


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G   17G  1.1G  95% /
none                  624M  360K  624M   1% /dev
none                  628M  104K  628M   1% /dev/shm
none                  628M   92K  628M   1% /var/run
none                  628M     0  628M   0% /var/lock
none                  628M     0  628M   0% /lib/init/rw
/dev/sda5              51G  265M   48G   1% /home
/dev/sr1              884K  884K     0 100% /media/HPLAUNCHER
/dev/sdc1             917G   39G  832G   5% /media/ExtVideo


Ok well looking at this I am not sure why my / is filling up.  Once before I had myth keeping huge log files of several gigs.  What do you recommend?

---

### Post by mikewhatever on 2010-06-24
Try investigating it with the 'du' command.
```
sudo du -sh /*
```

or better still
```
sudo du -s /* | sort -nr
```

---

### Post by jodajen2 on 2010-06-24
> **mikewhatever said:**
> Try investigating it with the 'du' command.
```
sudo du -sh /*
```or better still
```
sudo du -s /* | sort -nr
```


40335358    /media
12037096    /var
2285688    /usr
237104    /lib
86872    /home
32800    /boot
15212    /etc
7780    /sbin
6804    /bin
476    /dev
200    /srv
136    /root
48    /tmp
16    /lost+found
4    /xorg.conf.new
4    /selinux
4    /opt
4    /mnt
4    /cdrom
0    /vmlinuz.old
0    /vmlinuz
0    /sys
0    /proc
0    /initrd.img.old
0    /initrd.img


I am not sure why but the mythtv logs are 6gigs.  It seems there are several 1.2 gig backend log files.

---

### Post by mikewhatever on 2010-06-25
6GB is quite a lot for logs, but I am not familiar with mythtv. In Ubuntu desktop, the logs in /var/log rotate. They get compressed after some time and deleted after 30 days. I've seen my /val/log reach 15MB, but the current size is only 7.5MB.

---

### Post by tgm4883 on 2010-06-25
whats the output of 

```
ls -l /var/log/mythtv/
```

---

### Post by jodajen2 on 2010-06-25
> **tgm4883 said:**
> whats the output of 

```
ls -l /var/log/mythtv/
```


-rw-r--r-- 1 root   mythtv           369701 2010-06-25 16:37 mythbackend.log
-rw-r--r-- 1 root   mythtv 1682792448 2010-06-24 08:11 mythbackend.log.1
-rw-r--r-- 1 root   mythtv 2939027165 2010-06-22 07:48 mythbackend.log.2
-rw-r--r-- 1 root   mythtv 1773412447 2010-06-21 08:01 mythbackend.log.3
-rw-r--r-- 1 root   mythtv       48969017 2010-06-19 07:52 mythbackend.log.4
-rw-rw-r-- 1 jeremy mythtv    7605816 2010-06-25 16:19 mythfrontend.log
-rw-rw-r-- 1 jeremy mythtv                   0 2010-06-11 00:34 mythwelcome.log

---

### Post by ian dobson on 2010-06-26
Hi,

logrotate usually runs at 6am (or around that time) and if the system isn't running at that time then the logs aren't rotated.

To the op , you can delete the old log files. Dependant on the options set for mythbackend myth can create very large log files (on my backend with the option -important,eit the backend creates 30-40mb logs per day).

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-06-26
something looks like it is broke. What is going on in the mythbackend.log file.

---

