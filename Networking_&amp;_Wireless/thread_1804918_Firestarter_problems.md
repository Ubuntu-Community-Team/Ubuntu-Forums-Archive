---
title: "Firestarter problems"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by hailholyghost on 2011-07-15
Hi all,

I have recently installed Ubuntu 10.04 on my lab's computer.

I cannot get other school computers to log in.  My /etc/hosts.allow file reads:

```
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
ALL : malatya02.chem.rochester.edu bluehive.crc.rochester.edu bgpfen.crc.rochester.edu 
192.168.1.102

```
This was enough for my lab's Red Hat 4 machines.  However, something else is wrong on this Ubuntu box.

1.  I installed Firestarter, and under the policy tab, I have set malatya02.chem.rochester.edu as one of the Allowed connections, and also under "allowed service" under port 22.  However, I cannot log in from that box: "connection refused".

2.  Also, my VPN connection no longer works upon installing Firestarter, despite the permissive traffic policy.  Only when Firestarter is stopped can I log in.

3.  When Firestarter is off, and VPN is on, other hosts, namely the lab computer, are no longer recognized.

In attempting to fix one problem, I have created two others while not solving the original.

Your help is greatly appreciated!
-Dave

---

### Post by collisionystm on 2011-07-15
First off, get rid of firestarter and use GUFW.

Firestarter is no longer supported.

Did you install the SSH server?

sudo apt-get install ssh

---

### Post by hailholyghost on 2011-07-15
Hi collisionystm,

Thanks so much for your prompt reply!  I thought that that was installed before.  I installed GUFW.  I can now log in from the other lab computer.

However, neither of my VPN clients are working: Ubuntu native or the one I got from [http://www.mattzuba.com/2011/04/l2tpipsec-in-ubuntu-10-04/](http://www.mattzuba.com/2011/04/l2tpipsec-in-ubuntu-10-04/).

Do you know why this might happen?

Thanks,
-Dave

---

### Post by collisionystm on 2011-07-18
> **hailholyghost said:**
> Hi collisionystm,

Thanks so much for your prompt reply!  I thought that that was installed before.  I installed GUFW.  I can now log in from the other lab computer.

However, neither of my VPN clients are working: Ubuntu native or the one I got from [http://www.mattzuba.com/2011/04/l2tpipsec-in-ubuntu-10-04/](http://www.mattzuba.com/2011/04/l2tpipsec-in-ubuntu-10-04/).

Do you know why this might happen?

Thanks,
-Dave


Does it connect with the firewall inactive?

If so you just need to create a rule to allow the traffic.

---

