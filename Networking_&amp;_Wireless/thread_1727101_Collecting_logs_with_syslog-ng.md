---
title: "Collecting logs with syslog-ng"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by clubsoda on 2011-04-12
Here's what worked for me.

Install package syslog-ng. [Package rsyslog will be removed.]
Add the following lines to **/etc/syslog-ng/syslog-ng.conf** (need sudo)```
source netsrc { udp(ip("0.0.0.0") port(514));
                tcp(ip("0.0.0.0") port(514)); };
destination std {
        file ("/var/log/$HOST/logfile.log"
                owner(root) group(adm) perm(0640) dir_perm(0755) create_dirs(yes)
        );
};
log {
        source(netsrc);
        destination(std);
};

```Restart the logging daemon```
sudo service syslog-ng restart
```If your network device is sending log files they should now be accumulating in **/var/log/**.*.*.*/logfile.log** where **.*.*.* is the originating IP address.

Where the firewall is blocking the messages, try```
sudo ufw allow 514
```
Finally, if the device you want to log is on the same internal network as your ubuntu machine and you have network-manager configured for Auto DHCP, you might consider moving to Manual mode with a static IP address so that the logs aren't lost whenever your router assigns you a new address. If the device is external, you'll probably need a port-forward or virtual server rule on the router.

This isn't meant to be a comprehensive HOW-TO. I just found that some of the info floating around the net was outdated or incomplete.

Please post back any corrections & improvements.

---

