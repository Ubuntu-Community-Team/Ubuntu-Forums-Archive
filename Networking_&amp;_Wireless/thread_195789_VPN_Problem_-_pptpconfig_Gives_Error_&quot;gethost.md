---
title: "VPN Problem - pptpconfig Gives Error &quot;gethostbyname HOST NOT FOUND&quot;"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by masinger53 on 2006-06-13
Hello, all:

Happens on  both my laptop and my desktop; laptop is wireless Xubuntu Dapper, desktop is wired Ubuntu Dapper; LAN to router (which is DHCP server), router to DSL modem, modem to the cloud.  Installed pptp-linux and pptpconfig as listed in the HOWTO on both  boxen.  When running pptpconfig (as root) on either machine, with identical VPN settings, IP, domain, login, etc., both get the above error when attempting to connect.

I know the connection information is correct because it is identical to the WinXP VPN info on that partition and the connection is successful there.

Seems like it should be a simple fix, something I've overlooked, probably.  I'm not a networking geek - any help would be appreciated.

Thanks,

M.A.

---

### Post by masinger53 on 2006-06-16
Finally, got this working -- I ended up removing and reinstalling pptp-linux & pptpconfig and doing it again and it worked. /shrug

---

