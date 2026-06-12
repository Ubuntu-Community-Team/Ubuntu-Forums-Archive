---
title: "Mounting &quot;etc&quot;, &quot;tmp&quot; &amp; &quot;var&quot; to another partition?"
date: 2010-02-15
forum: Mythbuntu
---

### Post by hhtmp88 on 2010-02-15
Dear all,

I have partitioned my 320GB drive into the following partitions:
1. boot partition:     /boot     ( 100MB )     ----- /dev/sda2
2. Program Partition:    /     ( 15GB )     ----- /dev/sda1
3. Data Partition:     /home     ( 240GB )     ----- /dev/sda3
4. Backup Partition:     ??     ( 40GB )     ----- /dev/sda6
5. swap partition:     swap     ( 5GB )     ----- /dev/sda5


my questions is:
-> how can I mount /etc, /tmp, & /var to the data partition /dev/sda3 ?


Thanks for any kind of help!
Rgds,

---

### Post by hhtmp88 on 2010-08-05
any news?

---

### Post by laffinet on 2010-08-05
I think you got your understanding of mounting the wrong way around.

You don't mount folders to partitions, you mount partitions to folders.

/etc, /tmp, /var are part of the / (root) partition. I suspect you want to have them on separate partitions. For that to happen you need one partition each for /etc, /tmp, /var and then mount those partitions to the respective folders in / (root)

---

### Post by hhtmp88 on 2010-08-06
Am I right that we cannot put more than one folder into the same partition?
-> i.e. one partition cannot be mounted to multiple folders?

-> actually I want to put all user data and system configuration (i.e. the folders /home, /etc, /tmp & /var) into one single partition

-> just like what I do in WinXP -- c: drive for programs and d: drive for data

---

### Post by laffinet on 2010-08-06
> **hhtmp88 said:**
> 
-> i.e. one partition cannot be mounted to multiple folders?
Correct.
> -> actually I want to put all user data and system configuration (i.e. the folders /home, /etc, /tmp & /var) into one single partition
/etc, /tmp, /var don't really contain user data.

I suspect that you think /var is user data because a default mythbuntu setup stores video, recordings etc. under /var/lib/mythtv.

This can easily be changed. You could set up /home so it's on its own partition, create folders in /home for video, recordings, etc. and then direct mythtv to those folders (backend setup -> storage directories).

That way you have your "data" on a separate partition.

Why do you want /etc, /tmp, /var on a separate partition ?

---

### Post by nickrout on 2010-08-06
you could symlink to somewhere within /home, but this will probably fail in relation to /etc because /etc is needed in the root partitoin at boot time, because that is where everything is configured. 

To put it another way and to illustrate it graphically, /etc/fstab has all the mount points. If /etc is not part of the / mount point the startup scripts will never know where to mount /home and the system will never find /etc/fstab (because it is symlinked to somewhere in /home, which cannot be found because... yeah it's circular isn't it?)

Not to mention of course that the first process run after the kernel boots is init, which has it's config in /etc/inittab. Now I think about it that's probably even more fundamental than what I said in the last paragraph.

Yes you could develop a system and modify a whole lot of fundamental files where /etc was not in the root partition, but frankly then you don't really have a *buntu system any more and you should probably develop your own distro.

So I wouldn't muck about with /etc. I suspect /tmp may also be needed at boot, although I am unsure. /var isn't afaik.

---

### Post by kja999 on 2010-08-06
A couple of things;
You can mount a partition in different folders.
Try making a couple of folders in /mnt/ then mount sda2 to both of them ...

If you create an fstab entry for the folders you wish to move (/etc), and have created the folder at the destination it will work.

You could look at instructions on moving /home which is the same principle.
Google it, I.e [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

Be careful though .....

---

### Post by laffinet on 2010-08-07
> **kja999 said:**
> You can mount a partition in different folders.
Try making a couple of folders in /mnt/ then mount sda2 to both of them 

Well, technically yes, but the result will not be what the OP wants, because those two folders will contain the same data, ie whatever is on sda2 will show in both folders.
Doesn't work if the aim is to have /etc, /tmp & /var on a separate partition.

---

### Post by nickrout on 2010-08-07
repeat, you cannot have /etc on anywhere other than the root partition.

---

### Post by hhtmp88 on 2010-08-07
Thanks all for your great comments!

The reason why I want to have one partition for program and one partition for data & system configuration is that:
-> if the system crash, I simply overwrite the program partition with the previously saved image to recover it
-> everything works without any further installation and configuration!
-> this works quite well for my WinXP computer!

Hope that some Linux Guru can make a distro that facilitate system crash recovery!

---

### Post by laffinet on 2010-08-07
> **hhtmp88 said:**
> -> if the system crash, I simply overwrite the program partition with the previously saved image to recover it
-> everything works without any further installation and configuration!
For that to work you only need /home on a separate partition. All your configuration files for programs etc. are saved in under your home directory, while the programs themselves are under root.
So in order for recoveries like you described above you need an image of your root partition. 
When you have a problem and the only way to fix things is recovering your image (less likely in linux, things can actually be fixed ;) and the system doesn't get clogged up like windows) you simply overwrite your root partition with your previously saved image and everything is like it was.

---

### Post by nickrout on 2010-08-07
> **laffinet said:**
> For that to work you only need /home on a separate partition. All your configuration files for programs etc. are saved in under your home directory,

no, system settings are in /etc, per user settings are in /home

---

### Post by laffinet on 2010-08-07
> **nickrout said:**
> no, system settings are in /etc, per user settings are in /home

Which gets backed up and recovered when he restores his root image, so everything still works.

---

### Post by hhtmp88 on 2010-08-07
> **nickrout said:**
> no, system settings are in /etc, per user settings are in /home

If my memory is good, Mythuntu stores its data in /var!


Hi laffinet!
------------
Another very important reason for separating program and data (including system configuration) into two partitions is that
-> to keep the program partition as small and light as possible
-> if /var is where Mythuntu storing its photos, audios and videos, which maybe in a size of hundreds of GB
-> you may encounter a backup storage issue for the program partition!

---

### Post by nickrout on 2010-08-07
> **hhtmp88 said:**
> If my memory is good, Mythuntu stores its data in /var!


Hi laffinet!
------------
Another very important reason for separating program and data (including system configuration) into two partitions is that
-> to keep the program partition as small and light as possible
-> if /var is where Mythuntu storing its photos, audios and videos, which maybe in a size of hundreds of GB
-> you may encounter a backup storage issue for the program partition!

There is no "program partition" Binaries are in /bin, /sbin, /usr/bin, /usr/local/bin and sometimes in /opt. Just like /etc, /sbin and probably /bin too have to be present on the root partition so you can boot.

mythbuntu places recordings where you tell it to, but by default it is /var/lib/mythtv/recordings. And by default it points mythvideo at /var/lib/mythtv/video and gallery to /var/lib/mythtv/pictures. But you can place them anywhere.

All such MYTHTV settings are stored in the database. The only exceptions are the mysql.txt and config.xml files which tell the frontend where the backend is and what username and password to use.

---

### Post by hhtmp88 on 2010-08-07
Hi nickrout!

Thanks a lot for your great information!

but pls. note that....
* what I mean "program partition" is the partition that I want to put all OS (i.e. Linux or Windows) and application program files

* and what I mean "data partition" is the partition that I want to put all Linux system configuration, application program settings, and data files

* Mythbuntu is just an example to show the requirement of /var to be considered in the data partition

---

### Post by nickrout on 2010-08-07
OK well I will make it clear one more time.

system config is in /etc

/etc must be in the root partition.

/bin and /sbin contain programs and must be in the root partition.

You therefore cannot separate "programs" and "configuration" files.

You CAN separate "data" - simply mount /var/lib as a separate partition, that will contain the /var/lib/mythtv stuff and the /var/lib/mysql which contains the database.

However you should be automatically be backing up the database via the script in /etc/cron.weekly.

---

### Post by hhtmp88 on 2010-08-08
Thanks Nickrout for your advice!

So in order to make program partition as small as possible, I have to use multiple partitions for data files, application and system configurations:

1. boot partition:     /boot     ( 100MB )     ----- /dev/sda1
2. Program Partition:    /     ( 15GB )     ----- /dev/sda2
    -> contains application program files in: /bin, /sbin, /usr/bin, /usr/local/bin and sometimes in /opt.

3. Data Partition1:     /home     ( ??GB )     ----- /dev/sda3
4. Data Partition2:     /etc     ( ??GB )     ----- /dev/sda4
    -> which contains system configurations
5. Data Partition3:     /tmp     ( ??GB )     ----- /dev/sda5
 6. Data Partition4:     /var     ( ??GB )     ----- /dev/sda6
 
7. swap partition:     swap     ( 5GB )     ----- /dev/sda7


This looks much complicated when compared to Windows OS, and I will face the problems:
-> how big should I allocate each of the data partitions?
-> what should I do if one of them is full?

---

### Post by nickrout on 2010-08-08
YOU CANNOT PUT /etc ON ANOTHER PARTITION FROM /.

I will not give any more help if you don't take it!

---

### Post by laffinet on 2010-08-08
How about this:

1. grub partition - as small as possible - only contains grub
2. root partition - 20GB
3. root clone - 20GB - to clone your current install. You can boot into this if you messed up you running install
4. swap - 1-4 GB, depending on your memory
5. home - as big as you can - houses all your data, user configuration, recordings, liveTV etc. Simply direct mythtv to the right folders

Note: /etc, /var, /tmp stay within your root partition

---

