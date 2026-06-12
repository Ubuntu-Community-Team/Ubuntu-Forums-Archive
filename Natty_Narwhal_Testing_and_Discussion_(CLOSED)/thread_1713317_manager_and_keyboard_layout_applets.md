---
title: "manager and keyboard layout applets"
date: 2011-03-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by OGpmpdog on 2011-03-23
Hi,

This may be off-topic, so sorry ahead of time.

I lost the network manager and keyboard layout applets after the latest indicator applet updates.

I've got 2 cirlces, lined through the middle.

I guess the signs mean, "No more NM or Keyboard layout applets...it's a minor annoyance, but the inconsistency is UGLY!

Also, the new wallpaper..well, I wish i would have had the choice of replacing the old with new.

---

### Post by uRock on 2011-03-23
Bump for move to its own thread.

---

### Post by Harry33 on 2011-03-24
Here is the bug report similar to this thread:
[https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/741640](https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/741640)

So, OGpmpdog, please install the latest GTK+2 packages (version 2.24.3-0ubuntu4), then reboot.

Here is another bug report:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/741385](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/741385)

---

### Post by Harry33 on 2011-03-24
Actually try downgrading this package:
libappindicator1_0.3.0-0ubuntu1
to the previous version:
libappindicator_0.2.99-0ubuntu1

That should bring the notification area icons back.

---

### Post by OGpmpdog on 2011-03-24
Thanks for the reply.

I tried to downgrade, and got the below message:

E: Version '0.2.99-0ubuntu1' for 'libappindicator1' was not found

Oh, I found the deb. file, and got "error, later version already installed"

Help

---

### Post by Harry33 on 2011-03-25
> **OGpmpdog said:**
> Thanks for the reply.

I tried to downgrade, and got the below message:

E: Version '0.2.99-0ubuntu1' for 'libappindicator1' was not found

Oh, I found the deb. file, and got "error, later version already installed"

Help

Download the package libappindicator1_0.2.99-0ubuntu1 from here:
[https://launchpad.net/ubuntu/+source/libappindicator/0.2.99-0ubuntu1](https://launchpad.net/ubuntu/+source/libappindicator/0.2.99-0ubuntu1)
Choose the correct build (32-bit or 64-bit) first.
Then open terminal and go to the directory where the deb package is.
Run in terminal (64-bit example):
```
sudo dpkg -i libappindicator1-0.2.99-0ubuntu1_amd64.deb
```

---

### Post by OGpmpdog on 2011-03-25
Harry33,

THANKS so much for your help!

I'm still learning that command line - it is the solution!

Everything is OK now, just need to figure out how to mark this as SOLVED.

:D

---

### Post by Mblackwell on 2011-03-25
It's not really solved though. Downgrading a package isn't really the final solution,

---

### Post by Harry33 on 2011-03-26
> **Mblackwell said:**
> It's not really solved though. Downgrading a package isn't really the final solution,

Yeah right, that is more of a workaround, a temporary solution to get things going.

---

