---
title: "minidlna creating strange ufw listening log"
date: 2012-05-23
forum: Multimedia Software
---

### Post by Flaggmann on 2012-05-23
I install minidlna using synaptic pkg mgr. adjust minidlna.conf to scan correct folders and display server name to tv etc.

When I check gufw when minidlna is running, there is an ip address as shown as listening on a very high UDP port (changes with restarts).  address is xxx.xxx.0.3  which is local net address block. The address is not assigned by router dhcp or any static assignment at all; according to all net tools ping etc it responds.

nmap of the internal net shows xxx.xxx.xxx.3 exists but does not resolve to a hostname.

any explanation why ??

thanks

---

### Post by Flaggmann on 2012-05-23
faulty dhcp ; corrected now  ok

---

