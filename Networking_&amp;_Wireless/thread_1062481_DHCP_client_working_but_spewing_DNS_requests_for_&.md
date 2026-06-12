---
title: "DHCP client working but spewing DNS requests for &lt;hostname&gt;.local"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by jjv on 2009-02-06
Our internal Ubuntu 8.04LTS notebook systems are configured to use DHCP.  Our DHCP server running on Solaris 10 gives these systems the proper IP address and correctly sets the domain name and name servers in /etc/resolv.conf.  All addresses resolve correctly and our DNS server has been tested from both internal points and external points and found to be properly configured.

The issue is that the Ubuntu notebooks are attempting to get IP addresses from our DNS server for host names "<hostname>.local" and "<hostname>.local.<domainname>".  These requests are coming at the rate of several hundred per second (as monitored by our firewall logs).  I can snoop the interface they are hitting on the DNS server as see all these requests coming in faster than they can be displayed on the screen

I need to know how to change the behavior of whatever process(es) is/are causing these DNS requests to be generated.

Here are what I have attempted unsuccessfully to stop this behavior.
  - Disable multicasting on all interfaces (ifconfig <interface> -multicast)
  - stop the avahi service from running (it was not running in the first place)
  - set the AVAHI_DAEMON_DETECT_LOCAL=0 in the avahi-daemon file (again not running in the first place).
  - Various manual edits of the /etc/hosts file

One thing I did notice was that the hostname and IP address were NOT in the /etc/hosts file.  But DHCP did set up the correct /etc/resolv.conf file.  Also the "hostname -f" command returns the correct FQDN as <hostname>.<domainname>.  And "hostname" correctly returns the machines name only.

I need to stop these ".local" DNS requests as they are hammering the DNS server and severely loading the network segments these machines are on.

Any help is appreciated.

---

### Post by jimv on 2009-02-07
Uninstall Avahi on the machines.  I'm fairly certain that is the problem, even though you have the daemon off.  If you look in your nsswitch.conf file, you'll see that the machines are still trying to resolve addresses with mdns.

Removing Avahi doesn't harm anything...I don't even think I've ever seen it used.

---

### Post by jjv on 2009-02-07
No, the /etc/nsswitch.conf file only lists "files dns" for the hosts entry

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

---

### Post by jjv on 2009-02-07
I was able to remove avahi and thus stop mDNS from running.  Following a reboot the 1000+ mDNS reqiests for IP resolution for <hostname>.local and <hostname>.local.<domainname> ceased.

Our DNS server that was pegged at 100% CPU is now running at 3% - 5%:D

Thank for the assistance.

---

