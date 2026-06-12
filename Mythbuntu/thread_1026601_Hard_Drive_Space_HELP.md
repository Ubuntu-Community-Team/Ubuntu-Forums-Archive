---
title: "Hard Drive Space HELP"
date: 2008-12-31
forum: Mythbuntu
---

### Post by dareofficer on 2008-12-31
Hello, I have Mythbuntu, working well, however I need more hd space with my normal ubuntu programs.

I have installed the gnome gui.  I have been installing other programs when I noticed I have no more HD space.  I assume Mythbuntu puts most of the HD space in the video area.  Is there a way to free some of this space and or add another hd?  I have 1tb hd, so space at this point it not an issue with videos.

Thanks

---

### Post by newlinux on 2008-12-31
YOu can delete some recordings, and add a second hard drive and then add that hard drive to your recording storage groups. You can also set myth to leave a certain amount of space always available to the filesystem (I can't remember where this setting is off the top of my head) which is useful if you keep your recordings on the same partition as your root filesystem.

---

### Post by dareofficer on 2008-12-31
Hard disc space for the recordings is fine.  I even have a 2nd hd I can add.  Is there a way to mount or give this 2nd hd space to ubuntu, rather than myth?  If anyone knows the command to allow more space to ubuntu, that is what I need.

Thanks

---

### Post by newlinux on 2008-12-31
I'm not sure I understand what your current situation is but...

If you add a second drive and don't setup a mythtv storage group on that drive then myth won't use it for recordings. By default I believe myth uses /var/lib/mythtv/recordings. 

I'm not sure what you mean by "allow more space to ubuntu." All space can be used by ubuntu. If you want to restrict what space myth recordings use you can setup a disk drive and/or separate partition or find the setting in myth that tells it to leave a certain amount of space available on the filesystem (not at my myth machine right now, but I know the setting is in there somewhere, I've used it before).

---

### Post by dareofficer on 2008-12-31
I also use my Mythbuntu, as my Ubuntu system.  I have a 1TB hd, that has put 980GB of space to my mythtv only.  

I have been installing normal linux files, and have ran out of space.  I want to take some of the space that is setup only for tv/recordings, and give it to ubuntu for linux.  Is this possible?  At this time having over 900 GB free for TV, I would like to gave about 100 gb for linux. (ubuntu 8.10)  My home folder is down to about 5mb.

---

### Post by newlinux on 2008-12-31
> **dareofficer said:**
> I also use my Mythbuntu, as my Ubuntu system.  I have a 1TB hd, that has put 980GB of space to my mythtv only.  

I have been installing normal linux files, and have ran out of space.  I want to take some of the space that is setup only for tv/recordings, and give it to ubuntu for linux.  Is this possible?  At this time having over 900 GB free for TV, I would like to gave about 100 gb for linux. (ubuntu 8.10)  My home folder is down to about 5mb.

Do you mean you have a dual boot mythbuntu/ubuntu system or that you have separate partitions? Otherwise what I wrote earlier still applies. It's all accessible by ubuntu.

To clear this up, what is the output of:
```

df -h

```

How are your mythtv storage groups setup?

All of my mythtv systems are used as both regular desktop systems or servers and for mythtv. I think this is what you are talking about, but I don't understand how you have restricted the base OS from using space on your drives unless you have done some partitioning and/or are dualbooting. In other words, how have you set the space as "mythtv only?"

---

### Post by dareofficer on 2008-12-31
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  8.1G  2.4G  78% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  384K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  2.8M  1.8G   1% /dev
tmpfs                 1.8G  1.1M  1.8G   1% /dev/shm
lrm                   1.8G  2.0M  1.8G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6             920G  115G  806G  13% /var/lib


No, I only have one system.  I have mythtv, and I installed gnome, and picked it instead of the myth gui.  The /dev/sda6 is big, I just want to put some of my space back into the /dev/sda1, it only has 12g I see.

---

### Post by newlinux on 2008-12-31
So you have partitioned your drive. This issue has nothing to do with what myth can "access" and what ubuntu can access (ubuntu can access both partitions) but rather what parts of the filesystem are on which partition. You've made all of the root filesystem on one 12GB partition. Before I get into resizing your partitions (which will require you to boot to a liveCD because you can't resize your root partition while it is being used) let me ask if you are sure you don't just have a lot of files (or large files) in your home directory? I install a fair amount of software on my machines, including KDE and Gnome and my root partitions are are usually 10GB and are rarely go past 5GB (I have a separate home partition and fileserver where I put user created files).

If this is not the case you will need to use something (I use gparted) from the liveCD to modify your partitions, and you'll want to backup all your data first. If this is the way you want to go I can give you more information or you can look it up...

---

### Post by dareofficer on 2008-12-31
I have gparted.  Can you explain how to setup it up?  I was able to free some space, by deleting wine.  I still only have 2gb now.  I would like to add about 20gb.  I agree I don't think I need much.

Thanks for your help.

---

### Post by newlinux on 2009-01-02
First you'll want to back everything up because you can lose data. You will want to boot into a Ubuntu (or whatever your preferred) liveCD (you can't resize mounted partitions) so that you can resize your root and /var/lib partitions. Then when in the liveCD run gparted to do the resizing.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

This is a good tutorial on resizing ext3 partitions but it doesn't use gparted. I recommend reading it even if you want to use gparted.

[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

---

### Post by dareofficer on 2009-01-02
got it going, thanks for all your help.

---

### Post by rodercot on 2009-01-03
> **dareofficer said:**
> got it going, thanks for all your help.

I am in the same situation and tried Gparted live yesterday, how did you expand the root, without destroying your swap and var/lib partitions. I have made a directoy called home in /var/lib and there are serveral files in there. I wish to keep also in my root /usr/src folder I have Linux 2.6.28 and then the new customs debs that the new kernel created and then headers for 2.6.27-7, 2.6.27-generic. 2.6.27-9, 2.6.27-9-generic, 2.6.28-ulitmate. some of this can probably go to make some room on / as well.

 Thanks,

 Dave

---

### Post by dareofficer on 2009-01-03
Well what I did was a easy way out.  I put in a 2nd hard drive.  I split the HD, into two partitions.  The one was for more space for my mythTV, and the other was for more space to my root.

#
# File: /etc/fstab
#
/dev/hdb1  /mnt/hdb1  ext3  defaults 1 2

Try this

---

