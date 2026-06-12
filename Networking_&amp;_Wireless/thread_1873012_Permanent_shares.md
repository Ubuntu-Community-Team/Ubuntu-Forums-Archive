---
title: "Permanent shares"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by drtanz on 2011-10-31
Hi i would like to make permanent shortcuts to shared folders on my windows 7 computer. They are folders on a single drive, I would like these folders to be always available from say the desktop of my ubuntu laptop. Similar to 'map network drive' in windows. How can I do this?

---

### Post by jmate24 on 2011-11-02
this is for 2 ubuntu machines. but it may help with windows.
go to: [http://ubuntuforums.org/showthread.php?t=1872904]("http://ubuntuforums.org/showthread.php?t=1872904")

to figure out how to enable samba and create a folder. then to use it as a drive you need to make your machine that has that folder into a network file server. 

just open synaptic and search for network file server. then install nfs-common portmap nfs-kernel-server on the machine with the shared folder.

on the nfs machine #1 with the terminal type:
```
sudo /etc/init.d/nfs-kernel-server start && sudo /etc/init.d/nfs-common start
```

then you have to configure the /etc/exports file:
the format of the file is:
*Directory   host(options)    # Comments*

go to the terminal and type:
```
gksudo gedit /etc/exports
```

then lets say you use the /public folder from the previous post that i pointed you to: (in the /etc/exports file)
```
/public (rw,insecure,all_squash)  #Public Directory
/public Your Computer Hostname(rw,squash uids=0-99)
```

then save the file and reboot.

then log in open a terminal and type:
```
sudo /usr/sbin/exportfs -a -v && sudo chkconfig nfs on && sudo chkconfig nfslock on
```

then to mount the directory automatically in ubuntu on the second machine.
```
gksudo gedit /etc/fstab
```

and type:
```
smb:///Your Computer Hostname(machine #1)/public  mountpoint nfs options(rw,hard,rsize=4096,wsize=2048,bg {for instance}) 0   0
```

save the file then reboot the second machine.
if that does not work then pm me and i will help you install auto fs so that you can mount it ondemand.

---

### Post by drtanz on 2011-11-02
Thanks, I'm a bit green with Ubuntu, I didn't really figure out how to do this in my case.

I imagine there should be an easier way to do this. It's so simple to do it in Windows, I cannot see it being a difficult procedure with Ubuntu.

---

### Post by Morbius1 on 2011-11-02
> **drtanz said:**
> Hi i would like to make permanent shortcuts to shared folders on my windows 7 computer. They are folders on a single drive, I would like these folders to be always available from say the desktop of my ubuntu laptop. Similar to 'map network drive' in windows. How can I do this?
You have 3 options ( well, this is Linux so you have at least three options :wink: ) :

** [1] Bookmark it.**

Open up Nautilus, browse to the remote share, then select Bookmarks > Add Bookmark. It will show up in the left panel of Nautilus sort of kind of like a "mapped drive" does in Windows. It's not really auto mounted however since you will have to open up Nautilus and select the bookmark to actually mount it.

** [2] Create an entry in fstab.**

This can get rather involved but it is the standard way of doing this sort of thing. 

** [3] Gigolo.**

That's not an accusation it's a utility. It's by far the easiest method and you might want to look at this mini-Howto on how to use it to automount your remote shares: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

If you are interested in the fstab method let us know.

---

