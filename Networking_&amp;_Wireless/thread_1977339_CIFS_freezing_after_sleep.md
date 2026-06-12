---
title: "CIFS freezing after sleep"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by Icculus on 2012-05-10
I have an old Toshiba Satellite. I can mount the shared directory from my Windows 7 machine using the following command:

sudo smbmount //192.168.1.145/e /media/WinShare/ -o ro,username=MyName

Problem is, when my laptop sleeps and wakes up, I can't do anything near that mount point.

For instance, if I run

ls /media/

the terminal will freeze.

Now, I could probably live with this, however it has a much worse effect. I can't shut down my computer. Every time this happens, I get an error when it is trying to force close all the running applications. I don't know the entire error line for sure, but I do know it is like:

CIFS Unexpected Lookup Error -512

This seems like a similar issue, but has no solution:

[https://answers.launchpad.net/ubuntu/+source/cifs-utils/+question/194700](https://answers.launchpad.net/ubuntu/+source/cifs-utils/+question/194700)


Any help would be greatly appreciated!

X@X-laptop: ~$ uname -a
Linux X-laptop 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i386 GNU/Linux

---

