---
title: "Cisco Anyconnect SSL VPN Client Certificate Error"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by gekkos on 2010-01-15
Hi,
I'm using the 32-bit version of 9.10
When I try to run 
/opt/cisco/vpn/bin/vpn connect servergateway
I got this error
Cisco AnyConnect VPN Client (version 2.2.0133).

Copyright (c) 2004 - 2008 Cisco Systems, Inc.
All Rights Reserved.


  >> warning: No profile is available.  Please enter host to "Connect to".
  >> state: Disconnected
  >> notice: VPN Service is available.
  >> registered with local VPN subsystem.
  >> state: Disconnected
VPN>   >> contacting host (servergateway) for login information...
  >> notice: Contacting servergateway.
  >> warning: Unable to process response from servergateway.
  >> error: Connection attempt has failed due to server certificate problem.
  >> state: Disconnected

I overlooked many posts and tried almost everything including
sudo ln -s /usr/lib/nss/libnssdbm3.so /usr/lib/libnssdbm3.so
und
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so

but still the same error.
Any ideas what I can do
Many thanks

---

### Post by casevh on 2010-01-18
Try installing "libcurl3 with OpenSSL" and/or "libsqlite".

casevh

---

### Post by gekkos on 2010-01-27
Many thanks
These packages are installed but the problem/error still exist

Any other ideas??
Greetz

---

### Post by casevh on 2010-01-27
I've been using the 2.4 version of the client without any problems. You may want to see if you can get that version. I haven't used the 2.2 version for a while. 

To track down missing libraries in the past, I've done

```
strace ./vpn connect xyz 2>/tmp/error.log
```

and then looked through the error.log to find the references to the libraries that are missing. For example, I have the following lines in my log file:

```
open("/opt/cisco/vpn/lib/libnssutil3.so", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libnssutil3.so", O_RDONLY) = 3

```
The AnyConnect client first looked for libnssutil3.so in /opt/cisco/vpn/lib, and then found it /usr/lib. Somewhere there is a reference to library file that can't be found.

casevh

---

### Post by gekkos on 2010-02-01
Many thanks,
Do you know where I can download this new version (2.4) ??

gekkos

---

### Post by DouglasAWh on 2010-02-04
> **gekkos said:**
> Many thanks,
Do you know where I can download this new version (2.4) ??


The Cisco website.

Also, libsqlite does not appear to be a package in Lucid.  Any suggestions on that?

EDIT: I'm guessing the package is actually libsqlite0: [http://packages.ubuntu.com/search?keywords=libsqlite&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=libsqlite&searchon=names&suite=lucid&section=all)

EDIT2: after looking at [http://ubuntuforums.org/showthread.php?t=855485&page=3](http://ubuntuforums.org/showthread.php?t=855485&page=3) it might be libsqlite3-0

---

