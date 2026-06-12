---
title: "problem changing network proxy configuration"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by mayon2000 on 2009-06-10
Hi Everyone,

I have a problem regarding network proxy configuration. When I tried to change the http proxy in the network proxy preferences, the following error message is displayed:

"Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/http_proxy/host' set in a read-only source at the front of your configuration path"

I also attempted to edit the proxy settings using configuration editor but the /system/http_proxy/host key is not writable and the following message is displayed:

"No database available to save your configuration: Unable to store a value at key '/system/http_proxy/host', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf"

Kindly help me on this issue. I am new to ubuntu and linux in general.

Regards,

hillel

---

