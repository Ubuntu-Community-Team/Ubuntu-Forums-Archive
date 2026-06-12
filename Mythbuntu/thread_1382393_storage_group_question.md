---
title: "storage group question"
date: 2010-01-15
forum: Mythbuntu
---

### Post by 4dognight on 2010-01-15
I am having trouble trying to figure out how I should setup the default storage.

Here is my setup in a nutshell.

mythbuntu 9.10

MBE( name=mb) with /var/lib/mythtv/recordings dir
SBE/FE( name=m1) with /var/lib/mythtv/recordings dir
SBE/FE( name=m2) with /var/lib/mythtv/recordings dir

What I am trying to accomplish is to have the MBE's default storage group consist of all 3 dirs as above.

I have the dirs from m1 and m2 mounted as samba shares on mb as /var/lib/mythtv/recordings_m1 and /var/lib/mythtv/recordings_m2 respectively.

The contents of the MBE SG is
/var/lib/mythtv/recordings
/var/lib/mythtv/recordings_m1
/var/lib/mythtv/recordings_m2

I removed the local dirs on both m1 and m2 from their default SG.

My understanding is then I have only 1 storage group for recordings.

I have tuners in all 3 servers. So what is happening is when a recording trys to use either of the share mounted dirs, it fails with a permission denied error, and cant record then.

I have successfully manged to create test files from the MBE in those dirs as the user that myth runs as. So I cant figure out why it gets the permission error.

If I add the local dir back to one of the SBE/FE, it records fine.

My eventual goal would be to have all recordings just go to the MBE. But until I get this figured out I have to keep my local recording dirs defined in the SBE/FE.

---

### Post by williammanda on 2010-01-15
First off...why are you using samba? Use NFS.
Second...do you have storage groups for recordings setup on each backend?

Your quote...**What I am trying to accomplish is to have the MBE's default storage group consist of all 3 dirs as above.** end quote. 
This will be partially accomplished if all the backends have storage groups setup but it won't be on the master backend...it will be the collective of all the harddrives of the backends. If you want all recordings on the master backend then have all the tuners on the master backend.

---

### Post by 4dognight on 2010-01-15
I use samba, as I have windows machines that also need access to the same drives.

I did/do have storage groups on each SBE/FE. It is the only way I can get recordings to work on them for now. I eventually would like only recordings to be stored on the MBE.

From what I have read, its not necessary to have all tuners only on the MBE, to have all recordings on the MBE. 

I think what I have should work, it is this permission error that is giving me the grief.

---

### Post by williammanda on 2010-01-15
OK I see what your saying but the recordings will be on the computer the tuner card is installed on. So unless I'm wrong you won't be able to have all the recordings on the master backend unless all the tuners are on the master backend. This is one of the functions of storage groups ie to be able to expand your storage capability throughout the network of the storage capability of the network of your computers. So based on that I'm not sure how samba can be used to access all the recordings at a central location from a windows unit from one location.

---

### Post by 4dognight on 2010-01-16
This is pulled from thr Mythtv wiki documentation on storage groups.

[I][B]Storage Groups are lists of directories that are used to hold MythTV recording files. By default, there is only one Storage Group, called "Default". 

Storage Groups are global, but can be overridden on a slave backend by creating a local Storage Group by running mythtv-setup on the slave. If a problem occurs and the slave backend is unable to use the desired Storage Group, it will fail back and try the directories defined in the master's Storage Group[/B].[/I] 

This would lead me to believe that the "norm" is **not** to use local storage dirs for a SBE.

I decided to turn on verbose logging on both BE. It did try to write the recording to /var/lib/mythtv/recordings_m1 on the MBE. Problem is, it got a permission error.

Here are the permissions on the dirs. 

rick@mythtv-mb:/var/lib/mythtv$ ls -ld rec*
drwxrwsrwx 3 mythtv mythtv 40960 2010-01-15 23:00 recordings
drwxrwsrwx 3 mythtv mythtv     0 2010-01-15 22:02 recordings_m1
drwxrwsrwx 2 mythtv mythtv     0 2010-01-15 20:29 recordings_m2

The backend runs as user mythtv.

mythtv   11371 11370  2 22:22 ?        00:01:06 /usr/bin/mythbackend 

Here is a snippet of log showing it trying to open the file.

[B]2010-01-15 21:00:10.804 Using profile 'Default' to record
2010-01-15 21:00:10.828 TFW, Error: Opening file '/var/lib/mythtv/recordings_m1/1008_20100115210000.mpg'.
                        eno: Permission denied (13)
2010-01-15 21:00:10.848 TVRec(1) Error: RingBuffer '/var/lib/mythtv/recordings_m1/1008_20100115210000.mpg' not open...[/B]


I then ran a test, where I removed all but the local dir on the MBE default group. Also, on the SBE it had no dir defined in its local default group. It looks like it tried to write it locally to the / dir!
It also failed with a permission error, but I can see why if it was /.

It looks like a BE, whether it is a slave or the master , can **only** write a recording **locally**. Even with storage groups. :(

---

### Post by tgm4883 on 2010-01-16
> **4dognight said:**
> This is pulled from thr Mythtv wiki documentation on storage groups.

[I][B]Storage Groups are lists of directories that are used to hold MythTV recording files. By default, there is only one Storage Group, called "Default". 

Storage Groups are global, but can be overridden on a slave backend by creating a local Storage Group by running mythtv-setup on the slave. If a problem occurs and the slave backend is unable to use the desired Storage Group, it will fail back and try the directories defined in the master's Storage Group[/B].[/I] 



Thats a misinterpretation of the MythTV wiki. Recording storage groups can only write to a locally mounted filesystem. If you don't have a storage group defined on your SBE, then it will use the path from the MBE SG locally, not over the network. You might be able to mount the MBE directory on the SBE and have it work that way.

MBE = Master backend
SBE = Slave backend
SG = Storage Group

---

### Post by 4dognight on 2010-01-16
> **tgm4883 said:**
>  Recording storage groups can only write to a locally mounted filesystem. If you don't have a storage group defined on your SBE, then it will use the path from the MBE SG locally, not over the network. .

This info is not mentioned in the wiki. I suggest having it added.
Although I still think storage groups are not global, if I have to mount it locally on each server. I would say that its global with only one BE.

---

