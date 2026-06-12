---
title: "Unable to mount location"
date: 2012-10-12
forum: Networking &amp; Wireless
---

### Post by Royalist on 2012-10-12
Can anyone help with  this please?

Since recently  installing 12.04 from a downloaded live CD onto my desktop computer, I have been unable to re-establish a network connection with my other local computer in Nautilus. I have once had the following message displayed: 

 "UNABLE TO MOUNT LOCATION
DBus error org.freedesktop.DBus.Error.InvalidArgs:Mountpoint Already registered"

The desktop has a wired connection to hub and the other machine is wireless connected. The latter still connects to the internet OK.
Previously, I was using Ubuntu 11.10 which the other machine is still using.

Samba 4 is installed, but I have since run ```
apt-get autoremove
``` and the following is an extract of the report:

```
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Is there a bug please??  Any comments or suggestions will be welcome, thanks.

---

