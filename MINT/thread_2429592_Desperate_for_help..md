---
title: "Desperate for help."
date: 2019-10-20
forum: MINT
---

### Post by m9991912 on 2019-10-20
Hi, I don't know if I'm posting in the right section. I guess I should preface this by telling you that I know absolutely nothing about Linux or computers in general. So, please explain things to me like I'm a 4 year old, pretty please.

So, my brother got me Linux when I bought a used laptop a few years ago. He said it was better than Windows, so I said ok. 
After two years of ZERO problems, last week, all my files were locked, and Mozilla was acting weird and I couldn't access my bookmarks, etc. 
I searched online and read about 'fsck' commands, and how they fix things, so I tried different 'fsck' commands that were recommended and that RUINED everything. Now, when I turn on my laptop,  I'm stuck in Grub Rescue, and I've tried every single combination that  I've seen from Youtube videos, forums, and I can't get back in. 


I'm  currently using a bootable USB stick with Linux and read about Boot  Repair, so I figured I'd try it out. I can't make any sense of what  the results mean. My laptop is still stuck in  the Grub Rescue when I start it up. Any idea of what I can do to get  back in? 

Here's the Boot Repair results - [http://paste.ubuntu.com/p/tFfdsSJHtK/](http://paste.ubuntu.com/p/tFfdsSJHtK/)

I've been to Disks, and checked/repaired the Filesystem, and it says it's OK. 
I just don't know if it's the Filesystem, or the Partition, I honestly don't know what the heck any of that means. I don't know what to do, and it's just causing me lots of stress. Any and all help will be appreciated. Thanks.

---

### Post by oldfred on 2019-10-20
Moved to Mint sub-forum since Mint 17.3.
It also looks like you have done little or no maintenance. Even Windows requires users to do maintenance.
You at least should have housecleaned old kernels.

Did you run a full fsck on sda1?
You also have error message on grub install.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

Then see if from Boot-Repair's advanced options you can do a full reinstall of grub and install a new kernel.

---

### Post by jeremy31 on 2019-10-20
Mint 17.3 is EOL as it was based on Ubuntu 14.04.  Only Mint 18.? and Mint 19.? are supported now

---

### Post by m9991912 on 2019-10-20
> **oldfred said:**
> Moved to Mint sub-forum since Mint 17.3.
It also looks like you have done little or no maintenance. Even Windows requires users to do maintenance.
You at least should have housecleaned old kernels.

Did you run a full fsck on sda1?
You also have error message on grub install.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

Then see if from Boot-Repair's advanced options you can do a full reinstall of grub and install a new kernel.

Hi, 

So, I put in 

```
sudo parted -l
```

 and got the following - 

```
Model: ATA WDC WD6400BEVT-2 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  636GB  636GB   primary   ext4            boot
 2      636GB   640GB  3947MB  extended
 5      636GB   640GB  3947MB  logical   linux-swap(v1)


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel?    

```


Do I ignore or cancel?
Also, when you say "change example shown with partition sda1 to your partition(s)", can you please explain how to do that exactly? Sorry, I really don't know anything about Linux or computers in general. This is all new to me.
Thanks.

---

### Post by oldfred on 2019-10-20
I changed example to sda1.
The example is just to show what you enter. And as an example it uses sda1. And since your partition is sda1, you can copy the example without having to make any changes.
Others seeing this thread, may have to change to a different partition to run fsck as it may not be sda1.

---

### Post by m9991912 on 2019-10-21
> **oldfred said:**
> I changed example to sda1.
The example is just to show what you enter. And as an example it uses sda1. And since your partition is sda1, you can copy the example without having to make any changes.
Others seeing this thread, may have to change to a different partition to run fsck as it may not be sda1.

Hi again,
I did the e2fck command you mentioned earlier, and got the following -

==================================
mint@mint:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.44.1 (24-Mar-2018)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      860149 inodes used (2.22%, out of 38830080)
        2002 non-contiguous files (0.2%)
         443 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 2/2/2
             Extent depth histogram: 821862/374
    53761923 blocks used (34.61%, out of 155318784)
           0 bad blocks
           4 large files

      667196 regular files
      152813 directories
          60 character device files
          27 block device files
           2 fifos
          40 links
       39814 symbolic links (37584 fast symbolic links)
         228 sockets
------------
      860180 files
=================================

I then tried Boot Repair and got the same message as earlier. a.k.a. - 

================================
An error occurred during the repair.

Please write on a paper the following URL:


[http://paste.ubuntu.com/p/9bbQnMQZfd/](http://paste.ubuntu.com/p/9bbQnMQZfd/)

In case you still experience boot problem, indicate this URL to:


[email]boot.repair@gmail.com[/email] 

You can now reboot your computer.


The boot files of [unknown Linux] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))



 ================================

Any idea of what I can do next? Thanks.

---

### Post by oldfred on 2019-10-21
Some of the errors are from flash drive installer sdb, which are not important. It is not always configured in a standard way.

Is this a very old computer?
Boot-Repair mentions the far from start of drive issue for kernels. have not seen that error for years as all new UEFI systems (since 2012) do not have that issue.
That is solved by having a smaller / (root) within the first 100GB of drive and separate /home (and swap) for rest of drive.

Also shows grub configuration issue.
Try using Boot-Repair's advanced mode and full reinstall of grub and new kernel.

Once you boot system, houseclean old kernels.

---

### Post by m9991912 on 2019-10-21
> **oldfred said:**
> Some of the errors are from flash drive installer sdb, which are not important. It is not always configured in a standard way.

Is this a very old computer?
Boot-Repair mentions the far from start of drive issue for kernels. have not seen that error for years as all new UEFI systems (since 2012) do not have that issue.
That is solved by having a smaller / (root) within the first 100GB of drive and separate /home (and swap) for rest of drive.

Also shows grub configuration issue.
Try using Boot-Repair's advanced mode and full reinstall of grub and new kernel.

Once you boot system, houseclean old kernels.


The laptop is from 2009 or 2010. Everything's been running well, and still is, except for this current problem.

When you say to go into Boot Repair and reinstall new kernal, how do you do that? When I go to option, the only thing mentioning kernals, is 1) Add a kernal option (with a list of weird words) and 2) Purge kernals then reinstall last kernal. Do I tick one of these boxes?

Also, how do you houseclean old kernels? Is there a terminal code for that?

Thanks.

---

### Post by oldfred on 2019-10-21
Purge kernels should houseclean all the old ones.

Normally:
Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

