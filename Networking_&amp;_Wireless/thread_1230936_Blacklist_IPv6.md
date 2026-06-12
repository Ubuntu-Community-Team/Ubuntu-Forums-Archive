---
title: "Blacklist IPv6"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by Ashin Sopaka on 2009-08-03
Please forgive the lack of links/references here.

On another thread and subsequent bug report, it is reported that IPv6 is automatically enabled in the Jaunty kernel, and as such seemed to have impacted the internet speed of some users. It was all very technical, and I am not sure if the "bug" was corrected at the kernel level, but some people reported that blacklisting IPv6 helped. The file to be modified is: /etc/modprobe.d/blacklist-alieses.conf.

[Update: network.dns.disableIPv6 in Firefox is set to <b>true</b>]

Quesion: In /modprobe.d, that file doesn't exist. Do I need to create a new file with the appropriate blacklist, or do I modify one of the other existing blacklist- files, which are:
blacklist.conf
blacklist-ath_pci.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf (using GNOME commander, this file is a different colour than the others)
blacklist-watchdog.conf

It's really difficult to tell in this country if slow internet speeds are my problem, or the government throttling bandwidth, thus, I would like to test this configuration to see if it helps at all.

Once again, I am grateful in advance for any help you can provide.

---

### Post by wirelessmonkey on 2009-08-04
IPv6 is NOT a module in Jaunty, it is compiled in. You cannot change any blacklist or configuration file to remove it, short of recompiling the kernel.

Previous to Jaunty, it was a module, and could be blacklisted.

---

### Post by superprash2003 on 2009-08-04
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by binbash on 2009-08-04
[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

---

