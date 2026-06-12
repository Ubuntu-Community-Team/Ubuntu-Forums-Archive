---
title: "[SOLVED] Unable to install mpd in Hardy"
date: 2008-10-11
forum: Multimedia Software
---

### Post by sagara on 2008-10-11
I have been unable to install mpd from the repositories in Hardy.

A simple 

```
sudo apt-get install mpd
```

yields the following error:

```
Selecting previously deselected package libmikmod2.
(Reading database ... 120217 files and directories currently installed.)
Unpacking libmikmod2 (from .../libmikmod2_3.1.11-a-6ubuntu3_i386.deb) ...
Selecting previously deselected package mpd.
Unpacking mpd (from .../mpd_0.13.1-3ubuntu1_i386.deb) ...
Setting up libmikmod2 (3.1.11-a-6ubuntu3) ...

Setting up mpd (0.13.1-3ubuntu1) ...
 * Starting Music Player Daemon mpd
[COLOR="Red"]problem opening log file "/var/log/mpd/mpd.log" (config line 11) for writing[/COLOR]
                                                                                         [[COLOR="Red"]fail[/COLOR]]
invoke-rc.d: initscript mpd, action "start" failed.
dpkg: error processing mpd (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I tried to see what was in the file /var/log/mpd/mpd.log but the file does not exist.

If I try tu uninstall mpd using apt-get I have to delete the file **/var/lib/dpkg/info/mpd.*** otherwise the uninstall will fail claiming it can't stop the mpd daemon.

Any ideas what is wrong? Is there a bug in the package?

---

### Post by jpkotta on 2008-10-11
Sounds like a bug in the package.  Try```
sudo mkdir /var/log/mpd
``` and reinstall.  Also, file a bug report.

---

### Post by sagara on 2008-10-12
Thanks for the tip jpkotta, but the directory does exist.  I went ahead and created the log file myself, granted all permissions to it and it still did not work.

How are other installing this? from source or something?

---

### Post by sagara on 2008-10-12
Ok I figured this one out.  Turns out some time back I had tried to manually compile mpd from source.  It seems I still have some left overs to clean up from that install.

After creating the file **/var/log/mpd/mpd.log** and changing the permissions on **/var/log/mpd/errors.log** (created on the prior install) mpd installed succesfully.

---

