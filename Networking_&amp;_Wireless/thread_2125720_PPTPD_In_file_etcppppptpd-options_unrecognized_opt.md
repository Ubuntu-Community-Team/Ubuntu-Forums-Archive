---
title: "PPTPD In file /etc/ppp/pptpd-options: unrecognized option 'remoteip'"
date: 2013-03-14
forum: Networking &amp; Wireless
---

### Post by gomezra on 2013-03-14
So, I installed and configured pptpd on a fresh Ubuntu 12.04 server.  It works with a basic configuration.  I basically followed these instructions.  I disabled encryption, and I omitted localip and remoteip, as it said they were optional:

[http://silverlinux.blogspot.com/2012/05/how-to-pptp-vpn-on-ubuntu-1204-pptpd.html](http://silverlinux.blogspot.com/2012/05/how-to-pptp-vpn-on-ubuntu-1204-pptpd.html)

That worked.  Now that I have tested that, I need to specify the IP addresses that my clients get.  I don't want to assign per login, but have them pull from a pool of addresses.  When I add the 'localip' or 'remoteip' configurations to the  pptpd-options file, I get an error and my client can no longer connect.

Here's what I added to the file:

remoteip 10.10.155.1-100

Here is the error:

Mar 14 16:50:27 qa-net01 pppd[1297]: In file /etc/ppp/pptpd-options: unrecognized option 'remoteip'
Mar 14 16:50:27 qa-net01 pptpd[1296]: GRE: read(fd=6,buffer=6075a0,len=8196) from PTY failed: status = -1 error = Input/output error, usually cause
d by unexpected termination of pppd, check option syntax and pppd logs

If I also add the following before remoteip:

localip 10.10.100.12

I get the same error, but 'localip' is unrecognized.

I am completely stumped.  I have found nothing after searching, and the man page clearly states that 'localip' and 'remoteip' are valid configurations:

[http://manpages.ubuntu.com/manpages/precise/man5/pptpd.conf.5.html](http://manpages.ubuntu.com/manpages/precise/man5/pptpd.conf.5.html)

Any ideas?

Thanks,

Ricardo

---

### Post by gomezra on 2013-03-15
Okay, I installed the OS again, followed a different set of instructions, and when I put the localip and remoteip settings back into the config, I got the exact same result.  The VPN works fine, until I add those settings in.

---

