---
title: "Ugrade to Ubuntu Meerkat caused problem"
date: 2010-08-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by saurabh_nnegi on 2010-08-20
Hello All, 

I have tried to update Ubuntu 10.04 to Meerkat and due to partial install. My system refuses to start now.

I am concerned about the data on machine, will using the Live CD help backup the Data.

Also will Windows OS be able to detect Ubuntu10.04 partitions.

thanks

---

### Post by louieb on 2010-08-20
You can use a Live CD to backup your data.

Windows will see the partitions - and depending on the file-system used  you may  be able to read/write to them with [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")  or [Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs") 


BTW This post belongs in the [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310")  section of the forum.

---

### Post by Iowan on 2010-08-20
Moved to Maverick Meerkat Testing and Discussion

---

### Post by VMC on 2010-08-20
> **saurabh_nnegi said:**
> Hello All, 

I have tried to update Ubuntu 10.04 to Meerkat and due to partial install. My system refuses to start now.

I am concerned about the data on machine, will using the Live CD help backup the Data.

Also will Windows OS be able to detect Ubuntu10.04 partitions.

thanks
This is the wrong time to upgrade, since we are still in the testing phase. There has been a few folks that tried to upgrade without success. I would suggest to create another ext partition and install Maverick there.

As far as Windows "seeing" any Linux partitions. No, it can't without installing external program. As suggested boot from a live distro and backup , either using partclone or clonezilla.

---

