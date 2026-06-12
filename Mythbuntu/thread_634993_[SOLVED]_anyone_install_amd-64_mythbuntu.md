---
title: "[SOLVED] anyone install amd-64 mythbuntu?"
date: 2007-12-08
forum: Mythbuntu
---

### Post by volkswagner on 2007-12-08
I have downloaded the direct download and torrent locations.  My iso passed md5sum yet when extracted or burned there is no boot file and there are alot less files compared to ubuntu desktop cd's.

Is this normal for amd64 versions?  My cd wont boot, not bootable.  here is the list of files when extracted. can i add missing files from the desktop cd?

[LIST]
[*]casper
[*]dists
[*]install
[*]isolinux
[*]pool
[*].disk
[*]md5sum.txt
[*]README.diskdefines
[*]ubuntu
[/LIST]

My desktop amd64 has all the above plus the following
[LIST]


[*]bin
[*]disctree
[*]pics
[*]preceed
[*]programs
[*]ubuntu
[*]autorun.inf
[*]start.bmp
[*]start.exe
[*]start.ini
[*]ubuntu.ico
[*]wubi-cdboot.exe
[/LIST]

---

### Post by uopjohnson on 2007-12-08
Here is what my amd64 disk looks like.  Are you sure you have your bios set right to boot from the CD?
```
jon@stonewall:/mnt/tmp$ ls -lah
total 42K
dr-xr-xr-x 8 root root 2.0K 2007-10-21 02:16 .
drwxr-xr-x 7 root root 4.0K 2007-08-31 20:02 ..
dr-xr-xr-x 2 root root 2.0K 2007-10-21 02:11 casper
dr-xr-xr-x 2 root root 2.0K 2007-10-21 02:08 .disk
dr-xr-xr-x 3 root root 2.0K 2007-10-21 02:11 dists
dr-xr-xr-x 2 root root 2.0K 2007-10-21 02:11 install
dr-xr-xr-x 2 root root  14K 2007-10-21 02:02 isolinux
-r--r--r-- 1 root root  11K 2007-10-21 02:16 md5sum.txt
dr-xr-xr-x 5 root root 2.0K 2007-10-21 02:11 pool
-r--r--r-- 1 root root  225 2007-10-21 02:02 README.diskdefines
lr-xr-xr-x 1 root root    1 2007-10-21 02:02 ubuntu -> .
```

---

### Post by volkswagner on 2007-12-08
I am certain the bios is set to boot from cd first.  I booted other live cd's and just installed xpmce2005

I don't know what the first two entries are on your list, when I veiw the contents of the extracted iso Including hidden files the list I provided is all I see.  I will try to burn another disk and see.  I think the torrent file I downloaded was a little larger, the iso shows 473.6 MB (496652288 bytes), 

This is driving me crazy.  Two machines I get no joy with mythbuntu.  The second is i386 on pent4 2.4ghz and I get installer crash is in described in my other post.  I am not sure if it is because the master backend is not running on the network.

---

### Post by uopjohnson on 2007-12-08
The nature of torrents makes it impossible to download a bad iso.  Make sure your download finished, but if that is the case then you may want to try burning the CD again at the slowest speed.  It always pisses me off to have to do that, but it seems to solve a lot of problems.

---

### Post by volkswagner on 2007-12-08
Thanks for the replies.  The new burn from the torrent is booting as we speak.  Hope all goes well.  This does not say much for the effectiveness of the md5sum checker as all the iso's showed good.

---

