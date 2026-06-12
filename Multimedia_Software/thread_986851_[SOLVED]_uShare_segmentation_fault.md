---
title: "[SOLVED] uShare segmentation fault"
date: 2008-11-19
forum: Multimedia Software
---

### Post by c$$lguy on 2008-11-19
I'm trying to run uShare on Ubuntu 8.04. I tried both binaries: from Ubuntu server and from SourceForge. I can get it loaded but then I try to access it from PS3 it terminates with "Segmentation fault" message.

> Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
UPnP MediaServer listening on 192.168.15.100:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/c$$lguy/.aMule/Incoming
Found 29 files and subdirectories.
Segmentation fault


My settings in /etc/ushare.conf are:

> USHARE_NAME=uShare
USHARE_IFACE=eth0
USHARE_PORT=49152
USHARE_TELNET_PORT=1337
USHARE_DIR=/home/c$$lguy/.aMule/Incoming,/home/c$$lguy/Documents/Music
USHARE_OVERRIDE_ICONV_ERR=yes
ENABLE_WEB=yes
ENABLE_TELNET=yes
ENABLE_XBOX=no
ENABLE_DLNA=yes

What is interesting it complains about eth0 but still works. PS3 can see it but when I try to access reports DLNA error 7531. What could be the solution?

---

### Post by goldfish2 on 2008-11-21
A few things for you to try:

First try other folders... it doesn't look like it ever makes it to finishing reading your second folder.  I'm not sure if that means it is crashing somewhere in your Incoming folder or your Music folder, but try each one individually, or better yet try another test folder with just one or two files in it, that perhaps doesn't use hidden folders like .amule or $'s.

The second thing I would do is upgrade to 8.10.  I wasn't able to get Ushare to work in 8.04, so I tried upgrading and it magically started to work.  I wish I could give you more details on why that is, but I have no idea what was fixed between the two versions.

~GoldFish

P.S. I now have Ushare working (for my xbox) and still get the "Interface eth0 is down.", so whatever that means, it apparently doesn't prevent it from still operating properly.

---

### Post by c$$lguy on 2008-11-30
I solved the problem by getting source for ushare and latest libupnp. It appeared that I had old version of libupnp. After I rebuild everything from the source everything worked like a charm.

---

