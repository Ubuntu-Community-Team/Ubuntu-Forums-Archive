---
title: "Disconnected smb shares trying to connect and causing high system load"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by lateralchaos on 2011-06-08
I am having a problem in which some disconnected smb shares seem to be causing a high system load. CPU, memory, disk, and network usage appear to be normal. When I check console output from tty7, I see over and over:

```
mountall: mount /home/ray/shares/stora [18440] terminated with status 1
mount error: could not resolve address for store: No address associated with hostname
```

The [xxxxx] has different numbers for each line.

Now, I know why this is occuring: I bring my laptop between home and work, which both have smb shares. The relevant fstab entry is as follows, which I adopted from a guide I found on the forums:

```
//stora/MyComputers/ /home/ray/shares/stora smbfs auto,credentials=/home/ray/.credentials3,uid=1000,umask=000,user   0 0
```

I know you can connect to the server through the gui, and set a bookmark, but that never worked the way I wanted it. 

Can I modify my fstab entry or the way "mountall" functions, so that it does not repeatedly try to look for the share? I'm not sure that the load being maxed out is a huge concern, but I can't help but think I could be getting a little more performance (or at least accurate monitoring).

---

