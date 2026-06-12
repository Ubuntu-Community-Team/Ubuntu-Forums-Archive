---
title: "Samba server, good write but bad read performance"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by wmd on 2010-03-18
Running Samba on Ubuntu Server, one Win7 machine connected via GBit switch.

What I've done:
-set both to Jumbo frames 9k
-fiddled with Samba socket options, to no avail
-set some options via sysctl (those are set the same for r/w, so I guess that's not the culprit for this asynchronous behaviour)

resulted in:
-writes TO the share at around 60MB/s (I guess thats hd limited, just a single TB drive, no raid)
-reads FROM the share stayed at 16-17MB/s, whatever I changed

Any ideas to solve this would be appreciated. ;)

---

### Post by jrssystemsnet on 2010-03-18
First step: undo all the tweaking you already did.  This hurts you at LEAST as often as it helps you; modern network stacks have yielded pretty good performance on gigabit for several years now.

For reference, I just went through this in another Samba performance thread; these are the results from me installing Samba 3.3.6 on a bone-stock FreeBSD 7.3-R machine, and accessing it across a gigabit LAN from a bone-stock Samba 3.4.0 installation on Ubuntu Karmic.

```
me@banshee:~$ sudo mount.cifs //192.168.0.2/test /mnt -ouser=me
Password:
me@banshee:~$ dd if=/mnt/1G.bin bs=8M of=/dev/null
128+0 records out
1073741824 bytes (1.1 GB) copied, 13.7859 s, 77.9 MB/s
```

Someone in that thread said that users frequently complain that GUI transfers are slower than command line transfers, so I did the same thing again with a Nautilus copy-and-paste.

[img]http://virtual.tehinterweb.net/livejournal/2010-03-18_Samba-performance.png[/img]

Note that in this case, we're bottlenecked by write performance on the client: there's no way to dump the file to /dev/null from Nautilus.

Anyway, people frequently get red-herringed on this topic because it's EASY to get bottlenecked by something OTHER than the network when futzing around with gigabit LAN, and the 'net is chock-full of extremely outdated tweak guides based on TCP stacks that have been obsolete for YEARS.  So the first step is, take a deep breath, undo EVERYTHING you did to the TCP stack (and to any smb/cifs connection options) on BOTH boxes... then figure out a way to avoid getting bottlenecked by your local filesystem on either end... THEN retest.

Once you do that, we can start over. :)

---

### Post by Objekt on 2010-03-18
Speculation: Could your problem have to do with the overhead of reading from an ext3 or ext4 volume to an NTFS volume?

One problem with that hypothesis: I would think writing from NTFS to an ext3/4 volume would be slow as well, for the same reason.

Copying from one NTFS volume to another on the same machine, I get sustained rates of 60-70 MB/s, under either Windows XP or Ubuntu 9.10.

I'll have to do some testing later, to see whether ext3->NTFS transfers (and vice versa) are significantly different from NTFS->NTFS or ext3->ext3 transfers.

---

### Post by jrssystemsnet on 2010-03-18
> **Objekt said:**
> Speculation: Could your problem have to do with the overhead of reading from an ext3 or ext4 volume to an NTFS volume?Nope.  Samba neither knows nor cares about the underlying filesystem; there's no "additional overhead" involved if one fs is different than the other.

Raw performance of each underlying filesystem in and of itself, of course, does matter.

---

### Post by wmd on 2010-03-18
> **jrssystemsnet said:**
> First step: undo all the tweaking you already did.  This hurts you at LEAST as often as it helps you; modern network stacks have yielded pretty good performance on gigabit for several years now.

For reference, I just went through this in another Samba performance thread; these are the results from me installing Samba 3.3.6 on a bone-stock FreeBSD 7.3-R machine, and accessing it across a gigabit LAN from a bone-stock Samba 3.4.0 installation on Ubuntu Karmic.

```
me@banshee:~$ sudo mount.cifs //192.168.0.2/test /mnt -ouser=me
Password:
me@banshee:~$ dd if=/mnt/1G.bin bs=8M of=/dev/null
128+0 records out
1073741824 bytes (1.1 GB) copied, 13.7859 s, 77.9 MB/s
```

Someone in that thread said that users frequently complain that GUI transfers are slower than command line transfers, so I did the same thing again with a Nautilus copy-and-paste.

[img]http://virtual.tehinterweb.net/livejournal/2010-03-18_Samba-performance.png[/img]

Note that in this case, we're bottlenecked by write performance on the client: there's no way to dump the file to /dev/null from Nautilus.

Anyway, people frequently get red-herringed on this topic because it's EASY to get bottlenecked by something OTHER than the network when futzing around with gigabit LAN, and the 'net is chock-full of extremely outdated tweak guides based on TCP stacks that have been obsolete for YEARS.  So the first step is, take a deep breath, undo EVERYTHING you did to the TCP stack (and to any smb/cifs connection options) on BOTH boxes... then figure out a way to avoid getting bottlenecked by your local filesystem on either end... THEN retest.

Once you do that, we can start over. :)

´Hmh, you don't happen to have the defaults around for:

 net.core.rmem_max
 net.core.wmem_max
 net.core.rmem_default
 net.core.wmem_default
 net.ipv4.tcp_mem
 net.ipv4.tcp_rmem
 net.ipv4.tcp_wmem

:D

Which is all I remember changing. The thing is why only the reads from the share would be so badly affected? I'm pretty ok with the writes though.

---

### Post by jrssystemsnet on 2010-03-18
> **wmd said:**
> ´Hmh, you don't happen to have the defaults around for:

 net.core.rmem_max
 net.core.wmem_max
 net.core.rmem_default
 net.core.wmem_default
 net.ipv4.tcp_mem
 net.ipv4.tcp_rmem
 net.ipv4.tcp_wmem

:D

Which is all I remember changing. The thing is why only the reads from the share would be so badly affected? I'm pretty ok with the writes though.

```
me@banshee:~$ sudo sysctl -a | egrep "net.(core|ipv4.tcp).(r|w)?mem.*"
error: "Invalid argument" reading key "fs.binfmt_misc.register"
error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'
net.core.wmem_max = 131071
net.core.rmem_max = 131071
net.core.wmem_default = 129024
net.core.rmem_default = 129024
net.ipv4.tcp_mem = 767424	1023232	1534848
net.ipv4.tcp_wmem = 4096	16384	4194304
net.ipv4.tcp_rmem = 4096	87380	4194304

```

There ya go; that's defaults for Karmic amd64.

As for why read performance sucks worse than write... well, that could be TCP stack problem, could be a Samba buffering problem, or could be a filesystem problem.  I tend to think it's a filesystem problem; are you certain the files you're reading from aren't heavily fragmented?  In particular, anything you got via the transmission bittorrent client is likely to be EXTREMELY heavily fragmented, as in 80,000 or more frags in a single file... which coincides pretty nicely with the read speed you said you were getting.

To try to troubleshoot this, since you can't read from /dev/zero over Samba, you might try this:

```
you@box:~$ sudo apt-get install pv
```

**pv** is acronymic for **pipe viewer** - it shows you a nice progress bar and estimated time-to-complete for ANY operation you can pipe through it.  If you didn't already know about pv... you'll be glad you do now. :)

OK, now...

```
you@box:~$ sudo cat /path/to/big/file | pv > /dev/null
you@box:~$ sudo cat /path/to/big/file | pv > /dev/null
```

OK, now you have a good idea what the local filesystem speed is for a normal read from the big file... and you've immediately tried doing it with the same file again, to see if running it through the filesystem cache helped any.  RIGHT NOW, while it should still be as fresh as possible in the filesystem cache, try accessing it over Samba from your other machine.

How does that speed compare with the local speed you got by cat-ing the file to /dev/null?

---

### Post by wmd on 2010-03-21
First of all thanks for your reply, without changing anything I installed pv (nice little tool indeed).

Reading the file into nirvana and measuring with pv resulted in:

```
702MB 0:00:22 [31,2MB/s]
```

with a improvement of 0.4MB/s from the first to the second try. Now I read the file from the client via Samba, which resulted in ~17MB/s. Since the writes to the share are full speed and unaffected I'm guessing it's some kind of Samba setting?! The files aren't fragmented at all, this is not a torrent partition which I'm reading from.

I rebooted in the meantime, it seems whatever I changed to the tcp stack didn't stick, everything was set as the default settings yout posted, except for net.ipv4.tcp_mem which was for all values set for roughly the half. So I entered your reference values and repeated the procedure, but it didn't change anything.

Edit: The 50-60MB/s are not correct it seems, I've got this value from a network traffic mini-app. The Windows file copy dialog shows 27MB/s which is pretty close to the directly measured read speed.

---

### Post by wmd on 2010-03-23
bumpety-bump.

---

