---
title: "vpnc works with command line but not config file"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by jameszhu on 2006-06-24
Hello,

  I got a problem with vpnc.  When I type 'sudo vpnc-connect' and input the gateway,  group id, group pwd, user id and user pwd,  it works perfectly.  But when I put all these info into /etc/vpnc/default.conf like these:
qingjia@home:~$ cat /etc/vpnc/default.conf
IPSec gateway 220.200.*.*
IPSec ID mygroupid
IPSec secret mygroupdpwd
Xauth username myuserid
Xauth password myuserpwd

  and then I type 'sudo vpnc /etc/vpnc/default.conf',  I was told 'vpnc-connect: response was invalid [1]: ISAKMP_N_UNEQUAL_PAYLOAD_LENGTHS(30)'

  What's the problem?

---

### Post by jlhughes on 2006-06-24
Why type 'sudo vpnc /etc/vpnc/default.conf'?

When you have created the default.conf, just type sudo vpnc-connect

The default.conf is used automatically.

---

### Post by jameszhu on 2006-06-24
the result of 'sudo vpnc-connect' is the same as 'sudo vpnc /etc/vpnc/default.conf'.

anyone knows what this error message mean?  did a google search but didn't turn out anything.

thanks.

---

