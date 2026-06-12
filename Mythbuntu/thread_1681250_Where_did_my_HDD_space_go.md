---
title: "Where did my HDD space go?"
date: 2011-02-03
forum: Mythbuntu
---

### Post by nhtrader on 2011-02-03
I just did a fresh install of Mythbuntu 10.10 (32bit) tonight b/c I made a fatal mistake in deleting a critical package.

So I was curious regarding how much space this install takes. I was thinking that in the near future that I would partition the HDD so that all recording would be relocated to /home/nhtrader so that the system would be separated from user data. This would enable me to reinstall without losing user data and recordings. 

But for now, it seems that I'm missing approx. 100Gb of HDD space.

So Here's what I discovered....

root@nh:/# fdisk -l
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008ac21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       89672   720285696   83  Linux
/dev/sda2           89672       91202    12285953    5  Extended
/dev/sda5           89672       91202    12285952   82  Linux swap / Solaris


root@nh:/# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            708982752   2474088 670494380   1% /
none                   1791460       268   1791192   1% /dev
none                   1797052         0   1797052   0% /dev/shm
none                   1797052       360   1796692   1% /var/run
none                   1797052         0   1797052   0% /var/lock
none                 708982752   2474088 670494380   1% /var/lib/ureadahead/debugfs

root@nh:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             677G  2.4G  640G   1% /
none                  1.8G  268K  1.8G   1% /dev
none                  1.8G     0  1.8G   0% /dev/shm
none                  1.8G  360K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  677G  2.4G  640G   1% /var/lib/ureadahead/debugfs


root@nh:/# du -hs
du: cannot access `./proc/5863/task/5863/fd/3': No such file or directory
du: cannot access `./proc/5863/task/5863/fdinfo/3': No such file or directory
du: cannot access `./proc/5863/fd/3': No such file or directory
du: cannot access `./proc/5863/fdinfo/3': No such file or directory
2.2G    


Why is available disk space so low?

It looks like I only have 640Gb Available and it is only using 2.4G. So why am I missing so much HDD space?

And I should note, I have not recorded one program yet and I have not transferred any media files yet. This info was produced after a clean install plus all upgrades. No multimedia files exist or any other user data.

Please explain these facts.

---

### Post by nickrout on 2011-02-03
If you are using ext2 or ext3 the system reserves space for the root user to allow some headway, that space can usually be reduced on a large disk, typically it is 5% by default. Your missing space is pretty well 5% - (677-2.4-640)/677

fix it ```
sudo tune2fs -m 1 /dev/sda1
```

reduces the figure to 1%

---

### Post by nickrout on 2011-02-03
ps you can get info on the current filesystem options by 

```
sudo tune2fs -l /dev/sda1
```

---

### Post by bhaverkamp on 2011-02-03
First 750GB disk really only has 698GB of space.
Next you have given 6GB over to swap space.

The remaining missing space is described here:

[http://ubuntuforums.org/showthread.php?t=1636659](http://ubuntuforums.org/showthread.php?t=1636659)

I think you will find all your space accounted for...

---

### Post by nhtrader on 2011-02-04
Thanks for the explanation. I can add that the system uses ext4.
I also tried the command
sudo tune2fs -l /dev/sda1
Can't make sense of the output. It's over my head. But, nothing wrong - no error msgs.

Haven't tried to reduce it to 1% yet. Waiting to try it later.


External thread mentioned: 

compute 5% of 677:
33.85 = 677 x 5/100

676.4 = 34 + 2.4 + 640 (close enough to 677 which is total size)

Sum of other partitions:
7.2 = 1.8 + 1.8 + 1.8 + 1.8

684.2 = 7.2 + 677

Computed total size equals 684.2 which differs from 698 (total HDD size)

Can't account for 13.8 Gb.


This is clearly much less than what I first thought. However, there still seems to be a discrepancy. 

Am I still doing something wrong?

---

### Post by nickrout on 2011-02-04
Make sure you are using the same units. df -H will give diffrent results to df -h

---

### Post by runeh76 on 2011-02-04
good place to clean:
check ur var/log if u see REALLY big logs
.gz logs u can delete

U have "only" 640GB left   :grin:

---

### Post by nickrout on 2011-02-04
Look at this line:

677G 2.4G 640G

5% of 677 is 33.85.

33.85+640+2.4 = 676.25 which is pretty well 677. Nothing is missing.

---

### Post by nhtrader on 2011-02-04
nickrout,

Yes. I did acknowledge that fact. Nothing is missing now that I know 5% is in limbo until I change it to 1% on /dev/sda1

But when I try to tally the space for the entire drive, I found a difference between the 684.2 and 698. Admittedly, this was much lower than I had first thought.

---

