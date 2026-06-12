---
title: "Cannot connect to network"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by aubu2 on 2010-12-14
Hello
I'm STUCK !! I am trying to connect to the network.
I'm using VMware Player 3.1.0 build-261024 running Ubuntu 10.04 LTS.  
1. I right click on the Network Manager icon the icon with 2 computers with a red x in it and select Edit connections.
2. I add a Wired connection 1 in the wired tab checked Connect automatically, check Available to all users and click apply.
3. I get a dialog that says Authenticate "System policy prevents modification of system settings ..... etc etc.
4. I click Authenticate and get the next dialog box that says Connection add failed.
Close it.
If I then repeat this process steps 1, 2 when I click apply nothing shows up in the Network Connections dialog 
and there is a set of keys shown next to the Network Manager dialog, which goes away after time.
I checked to see if I have a connection using ifconfig and it appears I do.
[EMAIL="user@ubuntu:~$"]user@ubuntu:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:6a:15:6b  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe6a:156b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:159449 (159.4 KB)  TX bytes:10147 (10.1 KB)
          Interrupt:19 Base address:0x2024 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18096 (18.0 KB)  TX bytes:18096 (18.0 KB)

Screen shots attached.
Can anyone please help ?
Thanks

---

### Post by drdos2006 on 2010-12-14
I copied this from a previous posting for future use. It may be of some help to you......


You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

Code:

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

regards

---

### Post by agarzon on 2010-12-14
I am not familiar with vmware in weendous, but can you check that the network device is connected? ON Vmware in Linux is at the bottom right corner of your window.

It is weird that the IP you are getting is 192.168.1.1 Usually that number belongs to the router....

---

