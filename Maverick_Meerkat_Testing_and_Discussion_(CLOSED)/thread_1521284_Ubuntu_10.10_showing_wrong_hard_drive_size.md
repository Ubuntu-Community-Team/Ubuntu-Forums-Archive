---
title: "Ubuntu 10.10 showing wrong hard drive size"
date: 2010-06-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by TheMixtureMedia on 2010-06-30
Hi there I am running 10.10 right now and since today it is telling me that I went from 22 gig hard drive (main drive) and went to 700 meg and I have not installed anything new but updates. Does anyone have anythoughts about this??

---

### Post by dabl on 2010-06-30
> **TheMixtureMedia said:**
> 

Does anyone have any thoughts about this??

Yes -- one of us is confused   :confused:

Open a terminal window.
```

sudo fdisk -lu
``` will list all of your hard drive partitions, and their sizes, measured in blocks and sectors.

Is anything different?  Installing an OS or software will not change any of this.

To look at the amount of hard drive / partition space being used, run

```
du -h
```

This shows occupied space in K and M and G.  A very handy way to use it is to change to the "/" directory, then run ```
du -h --max-depth=1 | sort -n
```  This will show you the major users of space, in descending order.

To look at remaining free space on your filesystems, run

```
df -h
```

---

### Post by TheMixtureMedia on 2010-07-02
Well today it went to 4.1 gig then when I did a reset it went to 3.5 gig so it went from 22 gig to under a gig to this now any ideas??

---

### Post by plucky on 2010-07-02
> **TheMixtureMedia said:**
> Well today it went to 4.1 gig then when I did a reset it went to 3.5 gig so it went from 22 gig to under a gig to this now any ideas??

It would help if you posted the results of the commands **dabl** posted.

Also 10.10 is still in alpha testing and most of the forum users would not have come across it so you might have more luck in the [Maverick Meerkat Testing Forum](http://ubuntuforums.org/forumdisplay.php?f=385) or hit the **Report Abuse** button and get the moderators to move this thread.

Good Luck

---

### Post by TheMixtureMedia on 2010-07-03
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e8e68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   965394044   482696991   83  Linux
/dev/sda2       965394045   976768064     5687010    5  Extended
/dev/sda5       965394108   976768064     5686978+  82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x948fc822

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  2930272064  1465136001   83  Linux

Disk /dev/sdg: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbd65d7cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *          63    62524979    31262458+  83  Linux

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000359ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63  1953520064   976760001   83  Linux

---

### Post by TheMixtureMedia on 2010-07-03
Not the right information it has wrong information in please delete

---

### Post by Iowan on 2010-07-03
Moved to Maverick Meerkat Testing and Discussion - as requested... :)

---

### Post by TheMixtureMedia on 2010-07-03
0	./.gvfs
1.2M	./.config
1.8M	./.fontconfig
1.9M	./.adobe
2.9M	./.openoffice.org
4.0K	./Documents
4.0K	./Downloads
4.0K	./.gnome2_private
4.0K	./Music
4.0K	./.nautilus
4.0K	./Public
4.0K	./.ssh
4.0K	./Templates
4.0K	./.themes
4.0K	./Videos
4.3M	./.gconf
4.3M	./.macromedia
5.7M	./.cache
5.9M	./.dvdcss
8.0K	./.nv
8.0K	./Ubuntu One
8.8M	./.local
16K	./.icons
16K	./.mplayer
16K	./.update-notifier
20K	./.netx
20K	./.update-manager-core
24K	./.gegl-0.0
24K	./.sane
28K	./.bogofilter
28K	./.qt
32K	./.dbus
37M	./.opera
44M	./.wine
56K	./.compiz
56M	./.mozilla
60K	./.gnupg
60K	./.pki
72K	./.mission-control
98M	./.evolution
108M	./.thumbnails
124K	./.gconfd
212K	./Pictures
212K	./.pulse
240K	./.icedteaplugin
268K	./.gnome2
308K	./.Skype
360K	./.lgp
428K	./.kde
556K	./.gimp-2.6
612K	./.gimp-2.7
624M	./Desktop
708K	./.gstreamer-0.10
984K	./.clamtk
1006M	.

---

### Post by TheMixtureMedia on 2010-07-03
wrong info again

---

### Post by TheMixtureMedia on 2010-07-03
Right now I have 3.8 gigs and nothing but Ubuntu 10.10 on it do you guys need anymore info???

---

### Post by cariboo on 2010-07-03
Open a terminal and type:

```
df -h
```

And paste the results in your next post.

---

### Post by TheMixtureMedia on 2010-07-03
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdg1              30G   25G  3.9G  87% /
none                  3.9G  356K  3.9G   1% /dev
none                  4.0G  924K  4.0G   1% /dev/shm
none                  4.0G   96K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
/dev/sda1             454G  198M  430G   1% /2ndharddrive
/home/removed/.Private
                       30G   25G  3.9G  87% /home/removed
/dev/sdb1             1.4T  1.2T   85G  94% /media/Back Up System
/dev/sdh1             917G  200M  871G   1% /media/Back Up System 2
/dev/sr0              6.9G  6.9G     0 100% /media/cdrom0
```

---

### Post by TheMixtureMedia on 2010-07-03
Hey I just reseted my computer and it went from 3.8 gig to 3.9 gig right now

---

### Post by hikaricore on 2010-07-03
There are a few possibilities in this scenario.

1.  An application is temporarily storing files on your drive while it's running and using up some space. (less likely)
2.  An application is throwing a massive number of errors and a log file is eating up drive space. (likely)

To clarify what you're saying is before you had 22Gb of drive space and now you have between 3-4Gb of drive space and you've done nothing correct?

---

### Post by TheMixtureMedia on 2010-07-03
Well its a 32 gig drive (solid state) and all I really have in that drive is Ubuntu 10.10 (upgraded from 10.04). Also the drive is still telling me 3.9 gigs left and all my stuff is on a external drive. So I have no idea what is eating up everything and how to find out.

---

### Post by TheMixtureMedia on 2010-07-03
Ubuntu 10.10 is telling me I have a total of 129.2 TB (terabytes) (I wish I had that amount of space) and here is the proof of that.

---

### Post by cariboo on 2010-07-03
Open a terminal and type:

```
sudo apt-get autoremove
```

and then

```
sudo apt-get clean
```

to see how much free space that gains you.

---

### Post by TheMixtureMedia on 2010-07-03
Well I did what you said and that brought it from 3.9 to 4.5 but it still tells me I have 129 TB of HD space.

---

### Post by cariboo on 2010-07-03
What else is using up space? Have you checked trash in both your home directory and /root?

Also check /var/log to see if there any log files growing larger than they should.

---

### Post by TheMixtureMedia on 2010-07-03
I just checked and it says 18.5 gigs for all the files in that dir what can I delete??

---

### Post by TheMixtureMedia on 2010-07-03
I tried to delete it but it will not let me

---

### Post by TheMixtureMedia on 2010-07-03
Ok not sure here the dir said that there is 18.5 gig there and so I delete it and the trash can is empty and now it says I have only 17.5 gigs I still do not understand what else could I be looking for also it says 129.5 TB.

---

### Post by hikaricore on 2010-07-04
> ls -lahSr /var/log

This will list all the files in that directory showing the largest at the bottom of the output.
Try and make more sense with your posts and provide the information requested instead of rambling.

---

### Post by yelo3 on 2010-07-04
I also have the strange 128,1 TB issue when I go to filesystem properties :D

---

### Post by TheMixtureMedia on 2010-07-04
Ok I am sorry it was late for myself last night and I am sorry. I am not the only one with the TB issue so I know it is a 10.10 issue makes me feel better. Hey everyone that helped thank you and this should be marked as solved well at least for myself.

---

### Post by ronacc on 2010-07-04
a couple of questions , are you only having the problem with the ssd or with all of your drives ? and what file system are you using on that drive ?

---

### Post by TheMixtureMedia on 2010-07-04
I am using ext4 on all the drives and well not really sure about the other question on drive is 1 tb with nothing on it and ubuntu is telling me i only have 870 gb on it. My 1.5 tb looks right and my ssd is still telling me 15 gb.

---

### Post by ronacc on 2010-07-04
looking at your post# 12 on page 2 it looks line the only problem is with the ssd . The 1 tb drive looks about right , Ubuntu reports the total and avail space based on what actually can be used not the physical size of the drive , that is physical size - formatting and filesystem overhead. for instance my 2 500gb drives show 458.4 each , total size with ext3 .

---

### Post by yelo3 on 2010-07-04
No, I don't have a SSD.
The problem is not ext4 (I also have fedora which is detected correctly), the problem only appears when I go to the properties of "filesystem" and not other partitions.

---

### Post by TheMixtureMedia on 2010-07-04
Hey just to let you guys know the hard drive size just went from 15 gb to 1.3 gb and I just took it out of sleep mode. Also i looked at var/logs and nothing there that is over 5 meg. It came up with that warning that your HD size is getting small. I guess I jumped the gun when I thought it was fixed sorry.

---

### Post by hikaricore on 2010-07-04
Check your home folder as well.  Something is eating that space and I suspect it's an error log.
There's a tool somewhere that shows the drive usage by directory, but I can't recall the name of it..

There have been a lot of suggestions in this thread about what to check and how and you've only replied to a few of them with vague details.
Please be as thorough as possible if you ever expect to resolve this.

---

### Post by TheMixtureMedia on 2010-07-04
Hey I think I have covered what everyone has been telling me to do I have never tried to help out like this before and thought I was being helpful with feedback about 10.10 sorry I tried to help out. BTW I just reseted my computer and it says I have 23.3 gb back. From the 1.3 gb that I had on my ssd drive. Also I just checked my var/log dir and I only have 815.4kb in there right now and my trash is empty. Again thank you everyone for your help.

---

