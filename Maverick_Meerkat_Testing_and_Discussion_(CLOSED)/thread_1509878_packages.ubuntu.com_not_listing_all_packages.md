---
title: "packages.ubuntu.com not listing all packages?"
date: 2010-06-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2010-06-14
So for a while I've been searching for packages in Maverick to see if stuff is getting updates, and sometimes it comes back with no results found.

Example:
preload
audacious
lyx
deluge
bootchart

There are others but it was a while ago so I don't remember.

Is there a reason why some packages that are found in karmic/lucid are not shown in maverick?

I was gonna check to see if preload had any fixes since it hasn't [worked since Jaunty](https://bugs.launchpad.net/ubuntu/+source/preload/+bug/299361).

While I'm at it (instead of bumping another thread) if some people could see if preload works in Maverick that would be great.

---

### Post by kurros on 2010-06-14
I don't know why packages.ubuntu.com's search doesn't work for those... maybe because they haven't been explicitly uploaded to maverick yet. They are all there though.

For what it's worth I've been running preload since probably 2007 or so and haven't noticed anything broken. Guess i've been lucky.

> [Mon Jun 14 21:42:33 2010] 425950kb available for preloading, using 424300kb of it
[Mon Jun 14 21:42:33 2010] readahead 278 files


---

### Post by kurros on 2010-06-14
I just notice your post on that bug... seems it is probably working fine for you, but the default verbosity level for logging changed at some point during the karmic dev cycle to not show that Using 1234kb message.

I had to specify the -V option in /etc/defaults/preload to get the message back.

```
OPTIONS="-V 5 -l /var/log/preload.log"
```

Hope that helps.

---

### Post by andrewabc on 2010-06-18
> **kurros said:**
> I just notice your post on that bug... seems it is probably working fine for you, but the default verbosity level for logging changed at some point during the karmic dev cycle to not show that Using 1234kb message.

I had to specify the -V option in /etc/defaults/preload to get the message back.

```
OPTIONS="-V 5 -l /var/log/preload.log"
```

Hope that helps.

Thanks!!! That worked.

The correct location of the file is
/etc/default/preload

But not acting same as before (9.04). I am now getting
```
[Fri Jun 18 22:10:11 2010] state scanning begin
[Fri Jun 18 22:10:11 2010] state log dump requested
persistent state stats:
preload time = 4705770
num exes = 131
num bad exes = 1
num maps = 3937
runtime state stats:
num running exes = 61
[Fri Jun 18 22:10:11 2010] state log dump done
[Fri Jun 18 22:10:11 2010] state scanning end
[Fri Jun 18 22:10:11 2010] state predicting begin
[Fri Jun 18 22:10:11 2010] 571160kb available for preloading, using 353284kb of it
[Fri Jun 18 22:10:11 2010] readahead 751 files
[Fri Jun 18 22:10:11 2010] state predicting end
[Fri Jun 18 22:10:21 2010] state updating begin
[Fri Jun 18 22:10:21 2010] state updating end

```
Before it would just update the size and # of files. But at least this shows it is working. Maybe this is just a new way of displaying info.

---

### Post by andrewabc on 2010-06-26
Any news why programs and nothing is showing up when searching?

I'm forced to check packages.debian.org and assume it will be updated into ubuntu.

---

### Post by Umang on 2010-07-03
Is this the same problem as accessing [http://packages.ubuntu.com/maverick/](http://packages.ubuntu.com/maverick/) always resulting in this error?> 
[CENTER][SIZE="4"]**Error**[/SIZE][/CENTER]
more than one suite specified for show_static (dapper dapper-updates dapper-backports hardy hardy-updates hardy-backports intrepid intrepid-updates intrepid-backports jaunty jaunty-updates jaunty-backports karmic karmic-updates karmic-backports lucid)


Edit: BTW, I have been checking the [maverick upload queue]("https://launchpad.net/ubuntu/maverick/+queue") for "Done" items to track packages in Ubuntu.

---

### Post by andrewabc on 2010-08-25
I'm happy to inform others that it looks like packages.ubuntu.com is working for maverick.

I just searched for intel drivers and others and they show up, so I assume everything else does.

9.10 shipped with 2.9.0
10.04 shipped with 2.9.1
10.10 will ship with 2.12.0

So should be a big difference in drivers for intel users if upgrading from any ubuntu release. So going from 2.9.1->2.10(skipped)->2.11(skipped)->2.12 should be nice. Same can be said for linux kernel.

I'm interested to see Audacious using 2.4.0 RC2
Glad to see deluge updated to 1.3.0RC2
Sad to see scribusng not updated since 2009.

Lots of updated software for 10.10! :)

---

### Post by stone1343 on 2010-08-25
> **andrewabc said:**
> I'm happy to inform others that it looks like packages.ubuntu.com is working for maverick.

...

Lots of updated software for 10.10! :)

This is a good thing.

---

