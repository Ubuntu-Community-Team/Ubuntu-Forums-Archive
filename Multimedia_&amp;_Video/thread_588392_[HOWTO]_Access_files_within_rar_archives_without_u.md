---
title: "[HOWTO] Access files within rar archives without unpacking"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by andreeh on 2007-10-23
This is a guide on how to grab files inside a rar archive without actually extracting them (perfect for video streaming). Note that rar archives that are compressed does not work with this method, it's only for archives that used "store".

I've tested this on three different (freshly installed) Gutsy computers and they all ran fine. It should work on Feisty with this guide too.

**Disclaimer**: I'm not responsible for your system, everything in here is done by you and you're responsible for the things that might happen to your system.
Comments on how to make this guide better is very welcome, since I'm not all that good on user permits and these commands might compromise your system security (although I'm almost certain it won't).

Get the required packages (note that fuse-utils probably already is installed)
```

sudo apt-get install subversion automake1.9 fuse-utils libfuse-dev

```

Get the source code for our main attraction - rarfs - which is a virtual filesystem based on fuse
```

svn co https://rarfs.svn.sourceforge.net/svnroot/rarfs/trunk/rarfs/ rarfs

```

Lets build that code!
```

cd rarfs
./configure
make
sudo make install

```

Since fusermount comes pre-installed as root-only, we need to change a few owner and execution permits.
First off, add your user to the "fuse" group.
**NOTE**: The user you add to the group must relog after you added the user to it.
```

sudo adduser <user> fuse

```

Next up, make the group "fuse" owner on these files so we can access them.
```

sudo chgrp fuse /dev/fuse
sudo chgrp fuse /bin/fusermount

```

Now we must change the permissions on "fusermount", which we use to unmount our VFS without root access.
```

sudo chmod u+s /bin/fusermount

```

Now try
```

mount.fuse rarfs#/location/of/.rar/file /my/mount/dir

```
If no errors appear, you're all set!

You can unmount your rar archive by typing
```
fusermount -u /my/mount/dir
```

Here's a basic script that I'm using to just right click those .rar files and stream them directly.
```

#!/bin/sh
DIR=/home/`whoami`/rar.mount/
mount.fuse rarfs#$1 $DIR
gmplayer -fs -zoom $DIR`ls $DIR | grep .avi`
fusermount -u $DIR

```

Good luck! :P

---

