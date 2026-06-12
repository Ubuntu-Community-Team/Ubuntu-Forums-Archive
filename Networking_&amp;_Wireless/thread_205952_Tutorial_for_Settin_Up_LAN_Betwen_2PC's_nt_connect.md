---
title: "Tutorial for Settin Up LAN Betwen 2PC's nt connectd 2 net"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by gary4gar on 2006-06-29
hey guys...
I have two PC's ununtu 5.10 & Windows XP sp2 installed. got Lan cards intalled on both PC's. Got a LAN cable. The only reason for LAN is sharing data no NET..

I hope some of you techies will help me get this properly... i will be really thankful if a little bit detailed TUTORIAL is posted on this topic..

regards..
gary

---

### Post by Iowan on 2006-06-29
Unfortunately, few things (I hesitate to say *nothing*) are ever as easy as they seem.  Is the cable a standard  or a crossover cable?  From computer to computer, you'll either need a crossover cable, hub, or switch (or multiport router).   Sharing files from XP to Linux can be problematic if you're using the default file system (XPFS?).  Samba is the usual way to share files from Linux to Windows.  There are a couple of articles at [http://howtoforge.com]("http://howtoforge.com") that go through setting up a Samba server.

---

### Post by gary4gar on 2006-06-29
i have a crossover cable. see i also have to ntfs partions can they be shared.my root partions is ext3.

i have four partions

c:6.83 gb(fat32)(empty)(sharing needed)
d:6.52 gb(ext3)(linux)( no sharing)
e:30.43 gb(ntfs)(all data no os)(sharing needed)
f:30.43 gb (ntfs)(all data no os)(sharing needed)

my sole purpose is of data transfer from both computers

i searched the link u provided but no help

wainting for reply

---

### Post by Iowan on 2006-06-30
[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto]("http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto")
[http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+howto]("http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+howto")
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

Any of these help?
NTFS, not XPFS (sorry)... 
Unless things have changed, Linux can *read* files from NTFS, but *writing* is still  questionable. Along a similar vein, there's a program to allow Windows to read ext2 (write?) .  FAT32 can be shared by both.

---

### Post by gary4gar on 2006-06-30
thanx wonder full links
will try and then tell

---

