---
title: "No more space for OS / updates"
date: 2009-09-05
forum: Mythbuntu
---

### Post by HW_Hack on 2009-09-05
This is pretty F'd-up --- I installed the most recent mythtv on a PC acting as a combo setup with a 100GB drive. It setup an 11GB partition for the OS and the rest for myth. 

So I went to do an apt-get to download some files to get my DVD working and I've got zip space - gparted confirms this.

So I guess this is a FYI to not use the auto-setup on the partition ... now that I've got it 99% working I have to re-install.

---

### Post by movieman on 2009-09-05
My system has an 8.4GB system partition and 2.7GB free: so I think there's something odd in your configuration. You'll need to check for big files and delete them if you don't need them.

---

### Post by klc5555 on 2009-09-05
> **movieman said:**
> My system has an 8.4GB system partition and 2.7GB free: so I think there's something odd in your configuration. You'll need to check for big files and delete them if you don't need them.

The small 8-12 Gig root partition causes a fair number of difficulties, particularly if there is work to be done in the user's home directory (video/DVD editing, mytharchive temp files, etc. Or even non-PVR computer work.) I guess the arrangement has proved problematic enough that the partition distribution in 9.04 is supposedly being scrapped in 9.10 in favor of the normal Ubuntu arrangement, with one large ext4 partition for everything.

---

### Post by movieman on 2009-09-06
> **klc5555 said:**
> The small 8-12 Gig root partition causes a fair number of difficulties, particularly if there is work to be done in the user's home directory (video/DVD editing, mytharchive temp files, etc. Or even non-PVR computer work.)

I suspect that's the real problem, that one component that is configured to write files into the user's home directory has filled up the disk with one or more huge files. I never understood why so many parts of MythTV are configured to dump files into /home when the partition is so small.

---

### Post by geekyhawkes on 2009-09-06
The 9.10 configuration sounds alot more sensible than the multi partion installed of 9.04 IMHO.

---

### Post by HW_Hack on 2009-09-06
Yeah I agree that some process is dumping log files or building huge ones. While poking around I did something bad and now the database seems to be lost.

I think this time I'm going to do a regular 9.04 Ubuntu install and then load / install Mythtv. I had some other issues with over scan that may be solved by trying this.

---

### Post by williammanda on 2009-09-06
I install ubuntu then mythbuntu control center. This gives me a more all around computer. I like having a multi-purpose computer. Just installing mythbuntu limits the addons and not only that I like the gnome desktop.

---

### Post by jeremycobert on 2010-04-18
> **HW_Hack said:**
> This is pretty F'd-up --- I installed the most recent mythtv on a PC acting as a combo setup with a 100GB drive. It setup an 11GB partition for the OS and the rest for myth. 

So I went to do an apt-get to download some files to get my DVD working and I've got zip space - gparted confirms this.

So I guess this is a FYI to not use the auto-setup on the partition ... now that I've got it 99% working I have to re-install.

empty your trash in thunar then check your admin trash. gksudo thunar and empty that trash as well.

i once deleted some files as admin and forgot about it, they stayed in the trash and i ran out of space until i figured that part out.

---

### Post by ian dobson on 2010-04-18
Hi,

Have a look at what packages you can remove.

If you do a dpkg -l | grep linux from the terminal as root you'll see a list of all kernel's you've got installed.
```

dpkg -l | grep linux
rc  linux-image-2.6.27-14-generic              2.6.27-14.39                          Linux kernel image for version 2.6.27 on x86
rc  linux-image-2.6.27-7-generic               2.6.27-7.16                           Linux kernel image for version 2.6.27 on x86
rc  linux-image-2.6.27-9-generic               2.6.27-9.19                           Linux kernel image for version 2.6.27 on x86
rc  linux-image-2.6.31-16-generic              2.6.31-16.53                          Linux kernel image for version 2.6.31 on x86
rc  linux-image-2.6.31-17-generic              2.6.31-17.54                          Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-19-generic              2.6.31-19.56                          Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-20-generic              2.6.31-20.58                          Linux kernel image for version 2.6.31 on x86

```

Every kernel you can remove saves about 120Mb disk space.

If you do a uname -a you'll see the currently runing. You can delete a package with apt-get remove "PackageName".


A ii in the first column means the package is installed. rc means the package has been removed.

When you've removed all the unnecessary kernels, do a apt-get clean, apt-get autoclean, apt-get purge to clean up the mess. Also you could remove old log files from /var/log (*.gz *.0 etc)

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-04-18
I think based on the date and that the OP said he was going to reload the OS that the issue is resolved.

---

### Post by pu15e on 2010-04-19
Additionally, package files are (by default) cached in /var/cache/apt/ - emptying that folder often frees up a substantial amount of space ;-)

Cheers,
 Mattt.

---

