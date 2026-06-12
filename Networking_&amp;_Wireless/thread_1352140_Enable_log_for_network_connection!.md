---
title: "Enable log for network connection?!"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by Kjeldgaard on 2009-12-11
Hi

I have a wireless connection that keeps disconnecting. Sometimes it happens after 5 minutes and other times it happens after 5 hours. So I having trouble finding the cause of disconnecting. Is it possible to enable a log for the network? And using this log for troubleshooting/debugging.

I am running Ubuntu 9.10 kernel 2.6.31-16 and my usb dongle is a wusb54gc v. 3.

/Kjeldgaard

---

### Post by shredder12 on 2009-12-14
I think you will find something of your interest in /var/log/syslog (I am not on a linux system so i could be wrong). while you are connected run
```
sudo tail -f /var/log/syslog
```
this will give you a current update of the changes in that file.
when you disconnect you can check the output to see what actually happened.

and again I am not sure of the exact log file.. but you can do the same for any concerned file..

---

