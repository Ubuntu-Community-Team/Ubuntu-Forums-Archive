---
title: "fstab is going to get stabbed!"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by DracoJesi on 2009-10-05
ok observe this:

//127.0.0.4/ /media/Kody ext3 defaults 0 0

what is wrong with it? I've even tried the following....

//127.0.0.4/sda1 /media/Kody ext3 defaults 0 0

//127.0.0.4/sda1/home /media/Kody ext3 defaults 0 0

//127.0.0.4/home /media/Kody ext3 defaults 0 0

and then all those with 10.0.0.4

and replacing the ip with the server name......

I don't get anything, does the mount point have to be lower case, as in k not K

I'm going to go try it from the other side, and make sure I got the IP right.......

I have to move 30 some gigs of stuff xd

---

### Post by DracoJesi on 2009-10-05
```
root@Kody:/home/kody# mount //10.0.0.6/sda1 /media/Draco-laptop
mount: wrong fs type, bad option, bad superblock on //10.0.0.6/sda1,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I know it's an ext3 and when I try:

```
/home/kody# mount //10.0.0.6/sda1 /media/Draco-laptop ext3 defaults 0 0 
```

it spits out info about the mount command.......

and eth0 confirms that Kody is designated as 10.0.0.4

is this by chance a router problem?


and now back to Draco, to prove I'm not crazy.....

```
wlan0     Link encap:Ethernet  HWaddr 00:1d:d9:75:bb:b6  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:d9ff:fe75:bbb6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:910804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:638762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1229012354 (1.2 GB)  TX bytes:95329126 (95.3 MB)
```

.6! I knew it was.....

lets see, what else should I mention......

---

### Post by renkinjutsu on 2009-10-05
are you trying to mount a network share?
samba perhaps?

in that case, you shouldn't put ext3, you should put cifs for samba, or nfs or whatever you're using

---

### Post by DracoJesi on 2009-10-05
yep network share...... and I ditched Windows quite awhile back..... both systems are Jaunty

---

### Post by renkinjutsu on 2009-10-05
wait.. if both systems are running linux, then why use smb? :confused:

it's so slow (when running on linux at least) :(

me <- a big NFS advocate

---

### Post by DracoJesi on 2009-10-05
ok I'm confused, I thought that's what I was doing.... trying to use NFS

---

### Post by Iowan on 2009-10-05
[Here]("http://ubuntuforums.org/showthread.php?&t=283131") is a link on **fstab**, including a link for [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by DracoJesi on 2009-10-06
thanks guys... no wonder, I was using the wrong protocol :lolflag:

but this is worrisome:

> With NFS, a user's access to files is determined by his/her membership of groups on the client, not on the server

sounds like a security issue to me... hopefully I can select which computers can do this, and hope that method can't be fooled......... but then that leaves everyone else locked out :(

still reading......

also, if a user on your other pc, isn't root but is capable of sudo.... does that mean they can do anything as if they were root?

I'm going to try it, have it set up just locally.... and see how it goes but one more thing...

I have a third computer running on a liveCD, there is 30+GB of data I need moved over...... and there is only one optical drive (floppy isn't happening)..... before I can wipe the HD (actually that HD is NTFS but isn't running Windows either) and install Ubuntu...

how do I get the it working with live cd without user accounts? actually I think I'm going to have to use Samba aren't I? because that drive is NTFS even though the machine is running of of a Jaunty LiveCD?

---

### Post by DracoJesi on 2009-10-06
thanks guys, it's working now :)

now I just need to get that third pc networked..... find a blank disc and move on to Karmic with ext4 :)

---

