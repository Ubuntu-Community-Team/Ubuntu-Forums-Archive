---
title: "Intermittent Authentication Failures"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by binkbok on 2010-11-17
I am using netatalk 2.15 on a Ubuntu 10.10 machine. I am having users
connect from an Apple Time Machine client on their Leopard or Snow
Leopard machines.  The TMs attempt to connect once per hour.  5-7
times in a 24 hour period each of the clients will fail to be
authenticated.

Since operation is normal except for this intermittent error, I am not
sure where to start troubleshooting.  I have check afd.conf, and AppleVolumes.default.  No issues I can see, and since shares usually work. 

I don't know what places to check beyond the following

Nov 16 20:38:02 breganserver afpd[1391]: server_child[1] 3678 exited 1
Nov 16 20:38:02 breganserver afpd[3680]: AFP/TCP session from 192.168.1.4:58720
Nov 16 20:38:02 breganserver afpd[1391]: server_child[1] 3680 done
Nov 16 20:38:02 breganserver afpd[3681]: AFP/TCP session from 192.168.1.4:58721
Nov 16 20:38:02 breganserver afpd[3681]: DHX2 login: megan
Nov 16 20:38:03 breganserver afpd[3681]: PAM DHX2: PAM Success
Nov 16 20:38:05 breganserver afpd[3681]: DHX2: PAM_Error: Authentication failure
Nov 16 20:38:05 breganserver afpd[3681]: 0.51KB read, 0.38KB written
Nov 16 20:38:05 breganserver afpd[1391]: server_child[1] 3681 done

And from the client console:

Nov 16 20:38:23 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Attempting mount using
URL: [email]megan@breganserver.local[/email]/timeshare" target="_new">afp://megan@breganserver.local/timeshare>
Nov 16 20:38:26 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: FSMountServerVolumeSync
failed with error: -5023 for url:
[email]megan@breganserver.local[/email]/timeshare" target="_new">afp://megan@breganserver.local/timeshare>
Nov 16 20:38:26 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Authentication error -
the correct user or password info may not exist in the System.keychain
or the server may no longer allow access for this user.
Nov 16 20:38:31 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Backup failed with error:
29

Most of the time the client will authenticate properly:

Nov 16 19:38:03 breganserver afpd[1391]: server_child[1] 3643 exited 1
Nov 16 19:38:03 breganserver afpd[3645]: AFP/TCP session from 192.168.1.4:58071
Nov 16 19:38:03 breganserver afpd[1391]: server_child[1] 3645 done
Nov 16 19:38:03 breganserver afpd[3646]: AFP/TCP session from 192.168.1.4:58072
Nov 16 19:38:03 breganserver afpd[3646]: DHX2 login: megan
Nov 16 19:38:04 breganserver afpd[3646]: PAM DHX2: PAM Success
Nov 16 19:38:04 breganserver afpd[3646]: DHX2: PAM Auth OK!
Nov 16 19:38:04 breganserver afpd[3646]: login megan (uid 1001, gid 1001) AFP3.2
Nov 16 19:38:04 breganserver afpd[3646]: CNID server localhost:4700
Nov 16 19:38:04 breganserver cnid_dbd[3650]: Set syslog logging to
level: LOG_NOTE
Nov 16 19:40:00 breganserver afpd[3646]: logout megan

And on the client side:

Nov 16 19:38:23 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Starting standard backup
Nov 16 19:38:24 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Mounted network
destination using URL:
[email]megan@breganserver._afpovertcp._tcp.local[/email]/timeshare" target="_new">afp://megan@breganserver._afpovertcp._tcp.local/timeshare>
Nov 16 19:38:24 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Backup destination
mounted at path: /Volumes/timeshare
Nov 16 19:38:27 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Disk image
/Volumes/timeshare/Megan Michaels’s MacBook_0023df897602.sparsebundle
mounted at: /Volumes/Backup of Megan Michaels’s MacBook
Nov 16 19:38:27 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Backing up to:
/Volumes/Backup of Megan Michaels’s MacBook/Backups.backupdb
Nov 16 19:38:29 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: No pre-backup thinning
needed: 346.2 MB requested (including padding), 621.78 GB available
Nov 16 19:38:29 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Waiting for index to be
ready (906 > 0)
Nov 16 19:39:39 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Copied 388 files (29.8
MB) from volume Macintosh HD.
Nov 16 19:39:39 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: No pre-backup thinning
needed: 310.8 MB requested (including padding), 621.75 GB available
Nov 16 19:39:57 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Copied 310 files (259 KB)
from volume Macintosh HD.
Nov 16 19:40:02 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Starting post-backup
thinning
Nov 16 19:40:11 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Deleted backup
/Volumes/Backup of Megan Michaels’s MacBook/Backups.backupdb/Megan
Michaels’s MacBook/2010-11-15-184102: 621.79 GB now available
Nov 16 19:40:11 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Post-back up thinning
complete: 1 expired backups removed
Nov 16 19:40:11 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Backup completed
successfully.
Nov 16 19:40:14 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Ejected Time Machine disk
image.
Nov 16 19:40:21 megan-michaelss-macbook
/System/Library/CoreServices/backupd[46134]: Ejected Time Machine
network volume.

---

### Post by theosib on 2011-03-27
OMG, I've been fighting with this same problem on Gentoo for some time now, with no resolution.  Intermittent auth failures for Netatalk.

I filed the bug with Netatalk devs, but they told me that they wouldn't look into it unless someone paid them.  Also, they'd never heard of this before.

Since then, I've heard (a) that PAM is quite buggy, and (b) people who use kerberos only with Netatalk do not have this problem.

---

### Post by theosib on 2011-03-27
Some links to my bug reports:

[http://bugs.gentoo.org/show_bug.cgi?id=351863](http://bugs.gentoo.org/show_bug.cgi?id=351863)
[https://sourceforge.net/tracker/?func=detail&atid=108642&aid=3211262&group_id=8642](https://sourceforge.net/tracker/?func=detail&atid=108642&aid=3211262&group_id=8642)

---

### Post by binkbok on 2011-03-31
I ended up having to reinstall the OS.  I don't have the problem anymore, and my system has been stable for months.

No one has ever responded to my post, and I scoured the net for info for days.  I even talked to a linux development expert.

Sorry.

---

