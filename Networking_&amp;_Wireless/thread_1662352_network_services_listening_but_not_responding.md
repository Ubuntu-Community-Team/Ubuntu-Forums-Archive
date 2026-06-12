---
title: "network services listening but not responding"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by ramorrismorris on 2011-01-07
:confused:
After reboot required by kernel upgrade, for (at least) ssh and http, my services are running and listening, but apparently not responding
Ubuntu 9.04
kernel 2.6.31-22-server
removed and reinstalled openssh-server

0. ssh client on the same subnet or at a distance always times out.
1.   ps uax | grep sshd  shows sshd is running
2.  tcpdump shows kernel receives packets
3.  netstat shows there is a listener on port 22 with same pid as revealed in 1.
4. sshd_config has
  SyslogFacility AUTH and LogLevel VERBOSE
but no logs in /var/log seem to record any events associated in time with with the client request, nor does sshd_config suggest to me that logging might be in some other directory.
5. iptables are flushed
6. outbound ssh works fine, so I don't(?) suspect the network
7. restarting networking has no effect on the problem
8. sudo nmap -sV -p 22 <ip address> shows "Operation not permitted", but no entry in any log in /var/log corresponds to the scan time or packet id.
9. booting on either of the previous two kernels 2.6.31-20  or -17 has no effect on the problem, though I had a long successful run on each.
10. Power cycling the hardware has no effect on the problem 


Similarly for http

What the heck am I looking for????

Thanks
Bob

---

