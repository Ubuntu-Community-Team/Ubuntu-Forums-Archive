---
title: "Kismet: Capture source type 'b43' was not built"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by reltx on 2009-04-14
HELLO,

I'm trying to install kismet on my hp, dv6000 with a bcm4311.

I get this:
m@m-lap:~$ sudo -s
[sudo] password for m: 
root@m-lap:~# kismet
Launching kismet_server: /usr/local/bin/kismet_server
Will drop privs to m (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'b43' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
Done.


** My previous post was getting a bit long and I just did a clean install of ubuntu 8.10, and used the tut from here: [http://hacking-library.com/forum/viewtopic.php?f=36&t=26](http://hacking-library.com/forum/viewtopic.php?f=36&t=26)

---

### Post by chili555 on 2009-04-14
In order to read the tutorial, we have to register and log in. Sorry. What is wrong with kismet from the Ubuntu repositories, as I suggested previously?

---

### Post by reltx on 2009-04-14
I reinstalled it but got the same error:(

---

### Post by chili555 on 2009-04-14
May we please see the capture source section of your */etc/kismet/kismet.conf*? Also, does *sudo lshw -C network* confirm that b43 is the driver being used?

---

