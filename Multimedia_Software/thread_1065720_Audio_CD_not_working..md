---
title: "Audio CD not working."
date: 2009-02-10
forum: Multimedia Software
---

### Post by overlord.gaurav on 2009-02-10
I'm trying run an Audio CD that I just bought from the market. 
But, unfortunately it is not working on my system. 

When I try to open/mount the CD from my profile, it does open, but it doesn't play a single song. Also, all the files are owned by the root account.

When I try to open/mount the disc from the root profile, I get the following message:

```
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Trying the above command give the following output:
```
overlord@overlord-desktop:~$ dmesg | tail
[ 1488.111924] end_request: I/O error, dev sr0, sector 1108808
[ 1488.152737] end_request: I/O error, dev sr0, sector 1107560
[ 1488.797703] end_request: I/O error, dev sr0, sector 1248
[ 1488.856728] end_request: I/O error, dev sr0, sector 2496
[ 1488.908883] end_request: I/O error, dev sr0, sector 1248
[ 1488.967902] end_request: I/O error, dev sr0, sector 2496
[ 1488.967934] UDF-fs: No partition found (1)
[ 1489.090671] end_request: I/O error, dev sr0, sector 64
[ 1489.090827] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 1688.812380] uli526x: eth0 NIC Link is Up 100 Mbps Full duplex

```

I have attached the screenshots of the above.

---

### Post by ohgodnotanother1 on 2009-02-10
As far as I know Audio CDs do not contain a valid file-system, which can be mounted into the file-system tree.

I have found the following: [http://www.ii.pw.edu.pl/~borkowsm/cdfs.htm](http://www.ii.pw.edu.pl/~borkowsm/cdfs.htm)

You can listen to your Audio CDs with "Sound Juicer". It even lets you extract the content into .OGG or .MP3 files.

However it seems strange that your Audio CD contains .WAV files. :confused:

---

### Post by overlord.gaurav on 2009-02-10
Okay, the root problem continues. Its not really a problem though, because I do not intend to paly music through the root profile.
I installed Sound Jucier, and it play music from the CD, that's what I want it to do.

Thanks for reminding me of Sound Jucier!

---

