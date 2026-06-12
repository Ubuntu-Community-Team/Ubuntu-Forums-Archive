---
title: "vpnc segfault after 1 hour"
date: 2012-09-18
forum: Networking &amp; Wireless
---

### Post by rezunadol on 2012-09-18
I have an issue with vpnc where the tunnel stops working after approx one hour, I see a segfault msg in my syslog. I first upgraded because of a known bug, link below, but now the tunnel still stops working. The debugging does not help me further, while syslog reports a segfault at the time of the issue. vpnc does not stop, but traffic does not get through the tunnel anymore. I am not managing the other end of the tunnel (a Forti[net|gate] firewall), but I have no reason to expect the issue is originated there. I have "DPD idle timeout (our side) 0" in my config file.

Where should I start further troubleshooting or what hints do you have?

```

root@hostname:~# uname -a
Linux hostname.lcl 3.2.6 #1 SMP Fri Feb 17 10:34:20 EST 2012 x86_64 GNU/Linux
root@hostname:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
root@hostname:~#
```

I updated vpnc to prevent being stuck with this bug: [https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/479632](https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/479632)

```

root@hostname:~# apt-cache policy vpnc
vpnc:
  Installed: 0.5.3r449-2
  Candidate: 0.5.3r449-2
  Version table:
*** 0.5.3r449-2 0
        500 [http://64.repository.backtrack-linux.org/](http://64.repository.backtrack-linux.org/) revolution/main Packages
        100 /var/lib/dpkg/status
root@hostname:~# dpkg -i vpnc_0.5.3r449-2.1_amd64.deb
(Reading database ... 235791 files and directories currently installed.)
Preparing to replace vpnc 0.5.3r449-2 (using vpnc_0.5.3r449-2.1_amd64.deb) ...
Unpacking replacement vpnc ...
Setting up vpnc (0.5.3r449-2.1) ...
Processing triggers for man-db ...
root@hostname:~# apt-cache policy vpnc
vpnc:
  Installed: 0.5.3r449-2.1
  Candidate: 0.5.3r449-2.1
  Version table:
 *** 0.5.3r449-2.1 0
        100 /var/lib/dpkg/status
     0.5.3r449-2 0
        500 [http://64.repository.backtrack-linux.org/](http://64.repository.backtrack-linux.org/) revolution/main Packages
root@hostname:~#
```

Here is the segfault error from my syslog:
```

Sep 18 16:23:46 hostname kernel: [8387325.183607] vpnc[23776]: segfault at 62b33a ip 000000000040b16d sp 00007fff00f72050 error 4 in vpnc[400000+1f000]
```

I do run vpnc like this:
```

vpnc --debug 2 --no-detach configfile | tee vpnc-debug.txt
```

And my debug only tells this:

```

root@hostname:/etc/vpnc# tail vpnc-debug.txt
   lifetime status: 3584 of 3600 seconds used, 1|1330 of 0 kbytes used
   lifetime status: 3584 of 3600 seconds used, 1|1330 of 0 kbytes used
   lifetime status: 3584 of 3600 seconds used, 1|1330 of 0 kbytes used
   lifetime status: 3584 of 3600 seconds used, 1|1330 of 0 kbytes used
   lifetime status: 3584 of 3600 seconds used, 1|1330 of 0 kbytes used
   lifetime status: 3584 of 3600 seconds used, 1|1330 of 0 kbytes used
   lifetime status: 3584 of 3600 seconds used, 1|1330 of 0 kbytes used
   lifetime status: 3584 of 3600 seconds used, 1|1331 of 0 kbytes used
   lifetime status: 3585 of 3600 seconds used, 1|1331 of 0 kbytes used
   lifetime status: 3585 of 3600 seconds used, 1|1331 of 0 root@hostname:/etc/vpnc#
```

Where should I start further troubleshooting or what hints do you have?

---

