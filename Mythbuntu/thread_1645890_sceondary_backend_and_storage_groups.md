---
title: "sceondary backend and storage groups?"
date: 2010-12-15
forum: Mythbuntu
---

### Post by bance on 2010-12-15
Hi guys,

I'm trying to set up a secondary backend, I've got the cards and sources set up, I'm just a little unsure as to how I set up the storage directories. Do I have to set up samba mounts or will myth just use the directories on the master backend?

---

### Post by newlinux on 2010-12-15
If you set up all the directories properly in your master backend you shouldn't need to setup any for your secondary backend (even if you wanted the storage group  physically on your secondary backend). You do not need samba or NFS mounts.

This should help explain. 

[http://www.mythtv.org/wiki/Storage_Groups#Setting_up_Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups#Setting_up_Storage_Groups)

---

### Post by bance on 2010-12-15
Thanks newlinux,

I've read the wiki page at the link you posted,  and if I've understood it correctly,  all I need to do is add the path to the storage directories on the secondary b/e, to the storage group on the master b/e.

That is, the sbe. records locally to /var/lib/mythtv/blah/recordings and although that directory is not mounted on the mbe. storage groups includes the files.

?

once again thanks, Steve.

---

### Post by newlinux on 2010-12-15
> **bance said:**
> Thanks newlinux,

I've read the wiki page at the link you posted,  and if I've understood it correctly,  all I need to do is add the path to the storage directories on the secondary b/e, to the storage group on the master b/e.

That is, the sbe. records locally to /var/lib/mythtv/blah/recordings and although that directory is not mounted on the mbe. storage groups includes the files.

?

once again thanks, Steve.

Yes, add the the directories to the storage group on the master backend. By default if that directory exists locally to the slave backend that is recording, it will record it there (up to 2 simultaneous recordings - then what it does depends on how you setup balancing). Otherwise it will look on non local backends (like your master) for that and other directories in the mbe storage groups to record on. It will find the files to playback no matter where they are as long as the path to them is in the mbe storage group.

I hope that helps. It's not exactly straight forward, and I don't have a great way of explaining it.

---

### Post by nickrout on 2010-12-17
> **newlinux said:**
> Yes, add the the directories to the storage group on the master backend. By default if that directory exists locally to the slave backend that is recording, it will record it there (up to 2 simultaneous recordings - then what it does depends on how you setup balancing). Otherwise it will look on non local backends (like your master) for that and other directories in the mbe storage groups to record on.

No a sbe will NOT record on a MBE as described by you. storage groups do NOT specify the host, if a storage group directory does NOT exist on the sbe, that directory will not be used, at least according to the wiki. >  It will find the files to playback no matter where they are as long as the path to them is in the mbe storage group.

I hope that helps. It's not exactly straight forward, and I don't have a great way of explaining it.

---

### Post by bance on 2010-12-17
Thanks nickrout,

I tried adding the sbe recording directory to storage groups on the mbe, but got an error message, something like "warning file or directory doesn't exist is the path correct?". I suppose I have something incorrectly configured, Myth does recognise the tuner cards on the sbe though!

Maybe I had "Master backend overide" selected, I'll give it another go.

I'm not trying to record to the mbe, by the way, I just want all recordings to show up on the FE machines. 

I thought when I started out with Myth this should be pretty straight forward, How wrong can one be! Still, I don't think I'd have learned so much about Linux if I hadn't. Thanks to all involved with developing Myth, and of course all those users who share their knowledge so freely.

Steve.

---

### Post by tgm4883 on 2010-12-17
I haven't touched mythtv-setup in a while, but why wouldn't you just add the directory to the storage group on the secondary backend instead of the master backend?

---

### Post by newlinux on 2010-12-17
> **nickrout said:**
> No a sbe will NOT record on a MBE as described by you. storage groups do NOT specify the host, if a storage group directory does NOT exist on the sbe, that directory will not be used, at least according to the wiki.

Did you read the wiki part about scheduling where it talks about recording on local and remote drives?

[http://www.mythtv.org/wiki/Storage_Groups#Storage_Group_Disk_Scheduler](http://www.mythtv.org/wiki/Storage_Groups#Storage_Group_Disk_Scheduler)

What do you take this to mean? My interpretation was that after 2 local recordings it will record remotely based on the schedule option you picked. As a person who has 4 slave backends and 9 tuners, I should test this to see exactly what it does. I think maybe this assumes you have a remote directory that is mounted.

 I'm aware you don't specify the host in the storage group.  You do, however, pick which host to specify a storage group on, and whether it is a mbe or slave makes a difference. That's why the wiki says over and over 99% of users should only specify directories in the storage groups on the MBE.

If the storage group does not exist on the backend, of course it won't be used. but that doesn't mean it doesn't exist on other backends. This is where the difference between defining the storage group on the MBE and on a slave. If you define the directory on the slave it won't look for that directory on other machines. If you do it in the MBE it will. that's what I was saying EDIT: I'm still not being clear. By this I mean if the directories are specified in a storage group on the mbe, all slaves will look for that directory locally. If they are specified on a sbe storage, that's not true.

The only place I have specified storage groups on is my master backend. on each slave it looks for the directories I have specified in my storage group on the MBE. If it exists it uses it. If it doesn't it won't. I have no storage groups specified on remote backends.

---

### Post by newlinux on 2010-12-17
> **tgm4883 said:**
> I haven't touched mythtv-setup in a while, but why wouldn't you just add the directory to the storage group on the secondary backend instead of the master backend?

You can. And this would work. It's just the wiki goes out of its way on multiple occasions to tell you that this is most likely unecessary and certainly not preferred for most implementations.

---

### Post by newlinux on 2010-12-17
> **bance said:**
> Thanks nickrout,

I tried adding the sbe recording directory to storage groups on the mbe, but got an error message, something like "warning file or directory doesn't exist is the path correct?". I suppose I have something incorrectly configured, Myth does recognise the tuner cards on the sbe though!

Maybe I had "Master backend overide" selected, I'll give it another go.

I'm not trying to record to the mbe, by the way, I just want all recordings to show up on the FE machines. 

I thought when I started out with Myth this should be pretty straight forward, How wrong can one be! Still, I don't think I'd have learned so much about Linux if I hadn't. Thanks to all involved with developing Myth, and of course all those users who share their knowledge so freely.

Steve.

That message is okay. I get it too for directories that are on sbes but not on my mbe that I have specified in an mbe storage group. It still uses the storage groups correctly on my sbes. It's just a warning.

---

### Post by nickrout on 2010-12-17
I must say that the wiki is confusing, and to my mind contradictory in places. I must re read it when there aren't kids jabbering at me or killing the free world's enemies on xbox!

---

### Post by newlinux on 2010-12-18
> **nickrout said:**
> I must say that the wiki is confusing, and to my mind contradictory in places. I must re read it when there aren't kids jabbering at me or killing the free world's enemies on xbox!

It confuses the hell out of me too :).  But after re-reading it about 5 times this passage sticks out:

> For the situation where a Slave Backend has no storage and you use NFS or Samba, you may have all your storage on the master backend or some NAS or whatever. If so, just list all the directories in the Storage Group definition on the master backend and other hosts will use the same list of directories. Since all recording is done to "local" file systems, the remote file systems must be mounted at the same absolute path on all hosts. 

So I believe you are right, to record on remote systems, they must be mounted, and the storage group is smart enough to tell which systems are mounted from remote drives and which ones aren't. 

What threw me off is that other parts of the wiki say samba or NFS aren't needed and that scheduler will record to remote filesystems. Apparently it will only do that if youuse samba or NFS :).

---

