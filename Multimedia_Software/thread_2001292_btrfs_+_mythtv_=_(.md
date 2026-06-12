---
title: "btrfs + mythtv = :("
date: 2012-06-10
forum: Multimedia Software
---

### Post by yee379 on 2012-06-10
Hi, just want to report on some experiences and to see if anyone else has experienced similar.

i upgraded from 11.04 to 12.04 LTS about a month or so ago. the system i use is mainly for a htpc, so lots of storage ~10TB, not much cpu (2.8Ghz intel 775) and 4gb ram. as it's a htpc, i of course run mythtv backend and an xbmc frontend.

the upgrade went smoothly and everything appeared to work well. as i was migrating, i figured i'd make use of a spare hd lying around and doubled my mythtv storage/cache to 2 x 250GB (for the streaming and live tv recordings). aha! i'll use btrfs i thought in raid0-like fashion. everything went well and i left my system to do what it always does.

however, i began to notice that nearly all my recordings (whether they are high def or standard def) would begin to cut off after 10 or 20 minutes. mythtv 0.25 is buggy i thought! searched around and couldn't really find much. began to collect statistics using collectd and atop, and realised immediately that my IOWAIT was stupidly high. in addition (as a result?) my cpu load was immense (10.0+!).

after swapping in and out hardware, i finally decided after watching all the processes, that btrfs was at fault. i moved my mythtv cache to zfs and have had absolutely no issues since.

unfortunately, i also migrated my system disk to btrfs also... and because collectd is running and storing onto this, i still get a load of around 1.5 when doing nothing on the system.

i've never liked btrfs - never trusted the mirroring worked well, the tools always segfaulted, many many features are still missing (raid0->raid1 without 3.3 kernel?!). and to me, this puts another nail in it's coffin. unfortunately, the only other viable filesystem (zfs) also belongs to oracle. but with Mr. Mason moving companies, hopefully btrfs might get better. but i doubt it.

---

### Post by Derek Karpinski on 2012-06-12
Debian is working on combining GNU tools/userland with the freeBSD kernel.  That will allow you to run zfs.  [http://www.debian.org/ports/kfreebsd-gnu/index.en.html](http://www.debian.org/ports/kfreebsd-gnu/index.en.html)

Or run openindiana, or illumos.

---

### Post by yee379 on 2012-06-12
i'm using the native zfs module for linux actually :) i'm quote happy with it - even with the daily builds.

---

