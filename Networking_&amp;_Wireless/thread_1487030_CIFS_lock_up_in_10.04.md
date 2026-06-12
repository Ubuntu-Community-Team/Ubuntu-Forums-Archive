---
title: "CIFS lock up in 10.04"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by taz205 on 2010-05-18
I have 10.04 server (upgraded from 9.10) running on a box with a samba share from another box (8.04.2 desktop) mounted as

//web.lan/fs /mnt/smb/web.lan cifs defaults 0 0

Sometimes this works fine. When it works, I notice, however, the following message in dmesg log

CIFS VFS: server <ip of 8.04.2 host> of type Samba 3.0.28a returned unexpected error on SMB posix open, disabling posix open support. Check if server update available.

Other times, I don't get this error in dmesg and instead when I try to access the share (most often, a harddrive mounted into the filesystem of the host machine via /mnt/smb/web.lan/mnt/storage2/), the process attempting to access the share (ls or bash or whatever) will hang (using 100% of one of my logical cpu cores) but still be Runnable. And even though it's still runnable, it doesn't respond to "kill -kill" or "kill -15" or anything. What's even worse is that "shutdown -r now" doesn't do anything either, so I have no choice but to restart. (Which, funnily enough, I can't actually do now because I won't be physically at the box for another few hours...)

I can access the share in question from another machine (granted, a windows box) without any issues.

Am I right to assume this is an issue with CIFS module? I haven't been able to try disabling LinuxExtensions yet but even still, if it is a problem with CIFS module, shouldn't the module at least be clean enough to not hold the process in a state where I can't even kill -kill it?

---

