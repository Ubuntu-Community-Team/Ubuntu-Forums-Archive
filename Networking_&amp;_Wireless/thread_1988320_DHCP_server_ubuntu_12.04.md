---
title: "DHCP server ubuntu 12.04"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by fredou30 on 2012-05-27
Hello,

I'm presently trying to configure a DHCP server with Ubuntu 12.04
But I'm not able to make it work properly...

I can start it with : sudo start isc-dhcp-server
Gives me : start/running, process 3356

Then right after, if I execute : sudo status isc-dhcp-server
I'm getting : isc-dhcp-server stop/waiting

I've checked the logs (isc-dhcp-server.log), but they are empty.

Is this coming from a bad dhcp.conf configuration? 
Also, I can't even stop it, I'm getting "Unknown instance" message...

---

### Post by Lars Noodén on 2012-05-27
You could try starting [dhcpd](http://manpages.ubuntu.com/manpages/precise/en/man8/dhcpd.8.html) manually with the -d option for debugging.  That will keep the process in the foreground while routing output to stdout.  It should provide some insight into what's going wrong.

---

### Post by fredou30 on 2012-05-27
Problem solved!

Are review of /var/log/syslog there was an error with my config. Also there was a problem with the PID file.

I've had this line to my dhcpd.conf : pid-file-name "/var/run/dhcp-server/dhcpd.pid"

It's now working fine.

---

