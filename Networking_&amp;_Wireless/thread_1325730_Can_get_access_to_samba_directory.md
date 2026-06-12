---
title: "Can get access to samba directory"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by Cams on 2009-11-13
I've been scratching my head for two days trying to do a RAID 0 and create a shared folder for audio files. I followed this guide about creating shared directories and editing the smb.conf file:

[http://www.jonathanmoeller.com/screed/?p=1168](http://www.jonathanmoeller.com/screed/?p=1168)

I have a directory at /home/USERNAME/music and have the following entry for it in smb.conf:

```

[music]
path = /home/cams/music
available = yes
valid users = cams
read only = no
browsable = yes
public = yes
writable = yes

```

I created the RAID array md0. This tests as active. I put it in /etc/fstab as follows:

```
/dev/md0     /home/cams/music     ext3     defaults     1  2
```

It shows as mounted with the command df -h

It shows up in the network section in Windows 7 and I can double click to get in to the directory where I can see another directory called lost+found. However, when I try to copy anything into that directory, I get permission denied. 

I tried copying the procedure with another directory as follows:

mkdir /home/cams/test

I did the same settings in smb.conf as I did for /home/cams/music. I made sure to do sudo smbpasswd -a cams and used the same password that I use on Windows (the log-in is the same also, and on my Macbook). The test directory then appeared in Windows networking and I can copy files into it. 

So how come I can copy files into /home/cams/test but not into /home/cams/music? I can only guess that it has something to do with the fact that home/cams/music is mounted at /dev/md0

And I thought I was so close to getting this all done!

Any ideas?

And if I were simply to ignore the music folder and instead copy my audio files into home/cams/test, where would those files actually be going? Would they be going into the RAID array or into the parition set up for root?

---

### Post by cgb on 2009-11-13
the permissions on the drive itself must be different then the test folder.  what is the output of the below code for the two directories in question?

```
ls -l /home/cams/
```

---

### Post by Cams on 2009-11-15
I fixed it with chown from root to cams. Phew. All done. Thanks people.

---

