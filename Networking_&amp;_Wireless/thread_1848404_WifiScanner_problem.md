---
title: "WifiScanner problem"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by f.constantino on 2011-09-22
Greetings,

I'm doing some work in wireless security, and was recommended a program called WifiScanner. I need this to scan all the clients present in the vicinity of my AP.
I've downloaded the most recent version from SourceForge, but when I try to install it, it keeps saying the following:

```

root@fabio-laptop:~/Downloads/WifiScanner-1.0.1# ./autogen.sh 
        You must have automake 1.6 or later installed to compile wifiscanner.
        Download the appropriate package for your distribution/OS,
        or get the source tarball at ftp://ftp.gnu.org/pub/gnu/automake/
```And I've already verified, and I have version 1.11 of automake, which already comes with Ubuntu 11.04.
Anyone can give me some help please?

Thank you :)

---

### Post by chili555 on 2011-09-22
It probably really wants linux-headers-generic and build-essential as well as libltdl-dev, libtool and libncurses5-dev. Instead of autogen.sh, I suggest:```
./configure
sudo make install
```There were a lot of warnings. You might be better served with Kismet.

---

### Post by f.constantino on 2011-09-23
Humm, ty for the tip, kismet was indeed a very nice program :)

However I can only find APs and clients associated with those APs. My goal is to discover all devices with wifi turned on in the same room (in proximity of my laptop) regardless of if they are connected to a network or not, and send this information of discovered devices to an event handler. Does anyone know a program/API that lets me do this?

I've been looking for Java libraries with some functions to help me to this, but have been unsuccessful so far

---

