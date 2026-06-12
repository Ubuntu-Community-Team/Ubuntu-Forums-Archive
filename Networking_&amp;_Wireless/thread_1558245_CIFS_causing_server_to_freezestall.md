---
title: "CIFS causing server to freeze/stall?"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by stoiss on 2010-08-21
Hi,

I have a small home-server running Ubuntu server edition 10.04 LTS.

The server has mounted shares on a FreeNAS server (0.7.1 Shere (rev. 5127)). This worked fine in 8.04 LTS.

Ever since I upgraded to 10.04 I have been having problems transferring files to the FreeNAS server.

Sometimes the transfer stalls after a couple of gigabytes and sometimes it completes without problems.

Every time it fails I loose all network connectivity to the server and I have physically reset it.

I have no problems transferring the same files to and from my work station over SCP leading me to believe this is a problem with CIFS (ver. 1.12-3.4.7) rather than the NIC itself.

The syslog does not show any errors or warnings after the server is rebooted.


The command used to mount the shares on the FreeNAS server:
```

sudo /sbin/mount.cifs //<ipaddress>/<share> /mnt/<mountpoint>/ -o rw,iocharset=utf8,nounix
```

(for some reason this does not work without the "nounix" tag)


I have searched all over for an answer to this without finding anyone with the exact same problem or an answer to it :(

Any ideas to what could be the cause?

---

