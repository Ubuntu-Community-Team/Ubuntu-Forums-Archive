---
title: "Repository Connection Problem"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by mouse- on 2012-08-09
I'm not quite sure if this belongs here or in installation/upgrades, so if this is the wrong forum I apologise.  Somewhere around 2am last night I decided to turn on Polipo and PGL, but I fell asleep before I finished this.  When I tried to run the command apt-get update I got this error message: 
```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages  Unable to connect to 192.168.0.1:8123:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages  Unable to connect to 192.168.0.1:8123:

```
The error messages could take up pages, but what I believe it boils down to is that when I was editing the Polipo or PGL settings I somehow screwed up something.  I uninstalled Polipo and PGL in a sort of sleepy confusion this morning, which was probably not the brightest move.  I could undo the changes I made if I still had Polipo installed, but now I can't easily re-install it because I receive error messages every time I try.  All applications, however, can still access the Internet. 
 I am fully aware of the fact that this was all caused by my very bright  decision to mess with my computer while half-awake, but is there a way to fix this problem?

---

### Post by Laiquendi on 2012-08-09
Try reapairing your repositories (as you say you're connection is ok). Try to look at them and find what's messed up or just rewrite them.

---

### Post by mouse- on 2012-08-09
I checked my repositories, and no changes have been made to them since yesterday {and they worked yesterday}.  Just to make sure, what you meant by this was to check sources.list and look at each repository individually?

---

### Post by mouse- on 2012-08-12
I went into my network settings and made sure that the proxy was turned off and that solved the problem.

---

