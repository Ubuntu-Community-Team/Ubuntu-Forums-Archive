---
title: "storage group mounted drives not showing up 11.10"
date: 2011-12-29
forum: Mythbuntu
---

### Post by jeremycobert on 2011-12-29
hey all, I think I am going crazy... been working on this all day and made no headway.

i just reinstalled a fresh 11.10 install on my backend coming from 10.4. i have a 300gb drive as sata A. 

after i have it setup, i added three hard drives each one a 1TB drive . 
I mounted sata B as mnt/disk2
I mounted sata C as mnt/disk3
I mounted sata D as mnt/disk4

I set all the folders for mythtv as owner and gave permissions.

everything seems to be working except when I am in the backend and setup the storage groups.

for "default" I left the default group and then added each new drives location
mnt/disk2
mnt/disk3
mnt/disk4

now in 10.4 i used to have 4 drives each one would be listed. but now in 11.10 i have only 2 drives listed but drive 1 shows 3 separate folders where my drives are mounted..
like this
  [I]MythTV Drive #1:
        Directories: mythbox:/mnt/disk2, mythbox:/mnt/disk3, mythbox:/mnt/disk4
        Total Space: 938,899 MB
        Space Used: 47,893 MB
        Space Free: 891,006 MB
    MythTV Drive #2:
        Directory: mythbox:/var/lib/mythtv/recordings
        Total Space: 275,755 MB
        Space Used: 26,954 MB
        Space Free: 248,800 MB
[/I]

did something change or did i miss something ? its driving me crazy...... i should have roughly 3.3 TBs here like i did in 10.4.

if anyone can please help , I would be most appreciative.

---

### Post by nickrout on 2011-12-29
you say you listed them as mnt/diskX etc

Is that a typo? You seem to be missing the initial / as in /mnt/diskX

PS you shouldn't use the mount point as the storage group address. You should make a subdirectory like /mnt/diskX/recordings and use that as the SG directory. That way if the disk doesn't mount at boot for some reason (say it is damaged or removed) that dosk will not be recorded to. On your schema, if the disk isn't mounted, the system will record to your root file system and possibly fill your rather smaller hard drive.

---

### Post by cherry316316 on 2011-12-30
ok

---

### Post by nickrout on 2011-12-30
> **cherry316316 said:**
> I am also having the same problem.
when i use "gconf-editor" apps -> nautilus -> desktop -> volumes_visible
it says no schema installed for this thing.

i even copied all the ~/Home/.gconf files from my old computer, but still not working.
i reinstalled all the files in synaptic package manager under the headings "gnome", "gdm", and some other.

From my old computer, i compared some programs and install some of the missing files in my new computer, but nothing has changed :(

any suggestion will be appreciated.

what on earth has your post got to do with storage groups?

---

### Post by cherry316316 on 2011-12-30
ok

---

### Post by nickrout on 2011-12-30
> **cherry316316 said:**
> i have my windows partition mounted in my linux.
in my old computers, the windows drive and external drives are both visible on desktop as icon or shortcut. but i did fresh install of ubuntu 11.10 on my new computer and the icon/shortcut is not present on desktop.

i tried all the things i can to get the gconf updated, so that the values for "volume_visible" have proper links and stuff.

now, can u help ? if not that dont be so co*ky
thanks

Your problem has nothing to do with this thread, which is discussing storage groups, a feature of mythtv. Please go an post in a more appropriate forum.

Thanks.

---

### Post by jeremycobert on 2011-12-30
> **nickrout said:**
> you say you listed them as mnt/diskX etc

Is that a typo? You seem to be missing the initial / as in /mnt/diskX

PS you shouldn't use the mount point as the storage group address. You should make a subdirectory like /mnt/diskX/recordings and use that as the SG directory. That way if the disk doesn't mount at boot for some reason (say it is damaged or removed) that dosk will not be recorded to. On your schema, if the disk isn't mounted, the system will record to your root file system and possibly fill your rather smaller hard drive.

yes typo. i mounted the 1tb drives to /mnt/diskX
all of them are mounted and can be read/write to my mythtv.

as per your instruction, i created a folder on each called recordings and then set the storage group to /mnt/diskX/recordings.

rebooted and checked my status and its somewhat better, but still off, if you look at drive3 it has two directories so its still reading both of the hard drives as one drive with two folders. 

[I]Disk Usage Details:

    MythTV Drive #1:
        Directory: mythbox:/mnt/disk2/recordings
        Total Space: 938,899 MB
        Space Used: 47,921 MB
        Space Free: 890,978 MB
    MythTV Drive #3:
        Directories: mythbox:/mnt/disk3/recordings, mythbox:/mnt/disk4/recordings
        Total Space: 938,899 MB
        Space Used: 47,893 MB
        Space Free: 891,006 MB
    MythTV Drive #2:
        Directory: mythbox:/var/lib/mythtv/recordings
        Total Space: 275,755 MB
        Space Used: 26,874 MB
        Space Free: 248,881 MB
[/I]

nick, thanks for your help on this  !

---

### Post by ian dobson on 2011-12-30
Hi,

Firstly are the drives actually mounted correctly?Type df from the command line and you should see your drives :-

something like

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md0              19236244   6821908  12414336  36% /
udev                   8213900         8   8213892   1% /dev
tmpfs                  3288796      1016   3287780   1% /run
none                      5120         0      5120   0% /run/lock
none                   8221988         0   8221988   0% /run/shm
/dev/md1             7614249532 4194109624 3420139908  56% /data
```

In myth setup the storage dirrectories should be seperated by a ; I think.

Regards
Ian Dobson

---

### Post by jeremycobert on 2011-12-30
well this is strange, it automagically fixed itself.

i did some recording this morning of several shows to see which drives would get used, and when i looked up the status, it now shows all 4 drives.

I wonder if myth treats them as folders until it actually touches the drives with a file and then recognizes them as drives instead of just folders.

thank you guys for all your help !

[I]Disk Usage Details:

    MythTV Drive #1:
        Directory: mythbox:/mnt/disk2/recordings
        Total Space: 938,899 MB
        Space Used: 50,295 MB
        Space Free: 888,603 MB
    MythTV Drive #3:
        Directory: mythbox:/mnt/disk3/recordings
        Total Space: 938,899 MB
        Space Used: 48,425 MB
        Space Free: 890,474 MB
    MythTV Drive #4:
        Directory: mythbox:/mnt/disk4/recordings
        Total Space: 938,899 MB
        Space Used: 50,253 MB
        Space Free: 888,646 MB
    MythTV Drive #2:
        Directory: mythbox:/var/lib/mythtv/recordings
        Total Space: 275,755 MB
        Space Used: 34,534 MB
        Space Free: 241,221 MB[/I]

---

### Post by coblehome on 2012-01-02
I'm having a similar problem, I'll have multiple drives show up on one line of my Disk Usage Details and these can change with our with out rebooting, sometimes its just 2 or 3 drives, sometimes it 4 or 6 drives.  I have 9 drives total being used.  Below are some details and if I need some more just let me know .
Thanks.

MythTV Drive #1:
Directory: myth1:/storage
Total Space: 1,877,791 MB
Space Used: 1,870,636 MB
Space Free: 7,155 MB
MythTV Drive #2:
Directories: myth1:/storage10, myth1:/storage2, myth1:/storage3, myth1:/storage5
Total Space: 938,898 MB
Space Used: 934,903 MB
Space Free: 3,995 MB
MythTV Drive #4:
Directory: myth1:/storage4
Total Space: 938,898 MB
Space Used: 937,283 MB
Space Free: 1,614 MB
MythTV Drive #6:
Directory: myth1:/storage6
Total Space: 1,877,793 MB
Space Used: 1,873,801 MB
Space Free: 3,992 MB
MythTV Drive #7:
Directory: myth1:/storage7
Total Space: 1,877,793 MB
Space Used: 1,873,613 MB
Space Free: 4,180 MB
MythTV Drive #8:
Directory: myth1:/storage9
Total Space: 938,898 MB
Space Used: 934,997 MB
Space Free: 3,900 MB



MythTV Version   : v0.24.1-80-g1de0431
MythTV Branch    : fixes/0.24

Myth-status shows:
Disk Space:
Total space for group 1 is 1,833.8 GB, with 1,826.8 GB used (99.6%)
Total space for group 2 is 916.9 GB, with 913.0 GB used (99.6%)
Total space for group 4 is 916.9 GB, with 915.3 GB used (99.8%)
Total space for group 6 is 1,833.8 GB, with 1,829.9 GB used (99.8%)
Total space for group 7 is 1,833.8 GB, with 1,829.7 GB used (99.8%)
Total space for group 8 is 916.9 GB, with 913.7 GB used (99.7%)


@myth1:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdl5             6.9G  3.5G  3.1G  54% /
udev                  2.9G  8.0K  2.9G   1% /dev
tmpfs                 1.2G  1.2M  1.2G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  2.9G     0  2.9G   0% /run/shm
/dev/sdc1             917G  867G  3.9G 100% /storage2
/dev/sdh1             917G  635G  236G  73% /video1
/dev/sde1             1.8T  1.7T  7.0G 100% /storage
/dev/sdg1             1.8T  1.7T  4.1G 100% /storage7
/dev/sdf1             1.8T  1.7T  3.9G 100% /storage6
/dev/sdb1             917G  869G  1.6G 100% /storage4
/dev/sda1             917G  867G  4.0G 100% /storage3
/dev/sdk1             917G  867G  3.9G 100% /storage5
/dev/sdj1             917G  866G  5.1G 100% /storage9
/dev/sdi1             917G  867G  4.0G 100% /storage10

---

### Post by nickrout on 2012-01-03
> MythTV Drive #1:
Directory: myth1:/storage
Total Space: 1,877,791 MB
Space Used: 1,870,636 MB
Space Free: 7,155 MB
MythTV Drive #2:
Directories: myth1:/storage10, myth1:/storage2, myth1:/storage3, myth1:/storage5
Total Space: 938,898 MB
Space Used: 934,903 MB
Space Free: 3,995 MB
MythTV Drive #4:
Directory: myth1:/storage4
Total Space: 938,898 MB
Space Used: 937,283 MB
Space Free: 1,614 MB
MythTV Drive #6:
Directory: myth1:/storage6
Total Space: 1,877,793 MB
Space Used: 1,873,801 MB
Space Free: 3,992 MB
MythTV Drive #7:
Directory: myth1:/storage7
Total Space: 1,877,793 MB
Space Used: 1,873,613 MB
Space Free: 4,180 MB
MythTV Drive #8:
Directory: myth1:/storage9
Total Space: 938,898 MB
Space Used: 934,997 MB
Space Free: 3,900 MB

Where is that output coming from? What command line are you running?

---

### Post by coblehome on 2012-01-03
This part is coming from Mythweb under the backend status page. System Status -> Machine Status also shows the same thing when in Mythtv.

MythTV Drive #1:
Directory: myth1:/storage
Total Space: 1,877,791 MB
Space Used: 1,870,636 MB
Space Free: 7,155 MB
MythTV Drive #2:
Directories: myth1:/storage10, myth1:/storage2, myth1:/storage3, myth1:/storage5
Total Space: 938,898 MB
Space Used: 934,903 MB
Space Free: 3,995 MB
MythTV Drive #4:
Directory: myth1:/storage4
Total Space: 938,898 MB
Space Used: 937,283 MB
Space Free: 1,614 MB
MythTV Drive #6:
Directory: myth1:/storage6
Total Space: 1,877,793 MB
Space Used: 1,873,801 MB
Space Free: 3,992 MB
MythTV Drive #7:
Directory: myth1:/storage7
Total Space: 1,877,793 MB
Space Used: 1,873,613 MB
Space Free: 4,180 MB
MythTV Drive #8:
Directory: myth1:/storage9
Total Space: 938,898 MB
Space Used: 934,997 MB
Space Free: 3,900 MB

---

