---
title: "ntpdate: name server cannot be used"
date: 2012-06-06
forum: Networking &amp; Wireless
---

### Post by Shajik on 2012-06-06
Hi guys, I need a bit of tips on making work my Ubuntu 12.04 LTS x64 Server with bind + isc-dhcpd + ntpdate. I keep getting this error every reboot I do.

> May 13 23:37:13 srv01 ntpdate[723]: name server cannot be used: Temporary failure in name resolution (-3)All seems linked to /etc/default/ntpdate but even if mine is (I hope) well configured

> # The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.

# Set to "yes" to take the server list from /etc/ntp.conf, from package ntp,
# so you only have to keep it in one place.
NTPDATE_USE_NTP_CONF=no

# List of NTP servers to use  (Separate multiple servers with spaces.)
# Not used if NTPDATE_USE_NTP_CONF is yes.
NTPSERVERS="0.it.pool.ntp.org 1.it.pool.ntp.org 2.it.pool.ntp.org 3.it.pool.ntp.org"

# Additional options to pass to ntpdate
NTPOPTIONS="-u"
ntpdate seems to ignore the whole server stuff :/ Any1? If  u need a general look on my bind + isc-dhcp conf files, here's a [thread]("http://forum.ubuntu-it.org/viewtopic.php?f=28&t=521951") (Italian, but conf files are international, aren't em? :) ) Cheers

---

### Post by Shajik on 2012-06-07
Up! Help me please >.<

---

