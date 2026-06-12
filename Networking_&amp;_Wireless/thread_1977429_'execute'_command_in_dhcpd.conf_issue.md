---
title: "'execute' command in dhcpd.conf issue"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by nobluesky on 2012-05-10
this is my dhcpd.conf :


host PC2 { 
hardware ethernet D0:27:88:17:91:47; 
fixed-address 192.168.1.112; 
option host-name "PC2"; 
site-option-space "pxelinux"; 
option pxelinux.configfile "/PC2/default"; 
option pxelinux.pathprefix "/pxelinux/"; 
filename "gpxelinux.0"; 
execute("/root/test.sh"); 
}

when /root/test.sh contains non-root commands, it works without error.

but, if it has any of root commands(mkdir, rm ...) it doesn't work at all.

and my syslog is saying:


May 10 17:24:10 trex dhcpd: execute: /root/test.sh exit status 256


how can i fix it?

sorry for bad english.

---

