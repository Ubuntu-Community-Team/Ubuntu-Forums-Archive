---
title: "Fresh 10.10 install, DNS troubles"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by dcaunt on 2010-12-09
Hello everyone.  I apologize for the book I'm about to write, but I figured it would be best to include all the details I have for the following problem.   I just installed the system and there aren't many steps to mention in order to recreate the entire scenario which I have in front of me.

I recently installed Ubuntu 10.10 Server (my first Ubuntu Server installation) and it has been giving me DNS troubles from the beginning.  Sometimes it is able to connect to the DNS server and other times it cannot.  I'm assuming it's a misconfiguration because no other machines on the network are having DNS problems.  First, let me outline how I installed and configured the server.  Then, I'll explain the problem in detail and the steps I've taken to troubleshoot (with some output that might help).

**The Installation / Configuration**

During installation, I did a manual network configuration so that I could assign a static IP.  This seemed to work fine.  But later (after the installation) I manually changed the networking to DHCP because I learned that the IP for this server is a DHCP reservation, not a static IP.  I mention this in case it's important, but I ran into the same problems whether the machine was pulling the IP from the DHCP server or if it was statically assigned.

The only optional components that I chose during installation were "OpenSSH Server" and "Virtual Machine Host" (since I plan on installing virtual machine clients on this server later).

There are multiple Ethernet interfaces on this machine, so I followed the online documentation to change the logical names of the interfaces (so that the two main interfaces could be eth0 and eth1, instead of eth4 and eth5).  So, to do this I modified */etc/udev/rules.d/70-persistent-net.rules*.  I don't see how this could be causing any problems either, but I'm including all the steps I took since there aren't very many.

I set the network time by creating */etc/cron.daily/ntpdate* with mode 755 and contents "ntpdate -s time.nist.gov"

I added "AllowUsers dan" to */etc/ssh/sshd_config*.  I also added "UseDNS no" to */etc/ssh/sshd_config* once I noticed that it was taking a long time to connect via SSH.  Adding this line solved that issue.

I updated and upgraded the system using "sudo apt-get update" and "sudo apt-get upgrade"

I created an iptables-based firewall script called */etc/firewall* which I then saved with "iptables-save > /etc/iptables.rules" and set to load at boot time using */etc/network/if-pre-up.d* and */etc/network/if-post-down.d* as outlined in "Configuration at Startup: Solution #2" found here:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

**The Problem**

From the beginning (when I first logged in remotely via SSH) I noticed DNS issues.  As I mentioned above, I had to put the "UseDNS no" line in */etc/ssh/sshd_config* to fix the long delays I had while connecting.

The problem is basically this: sometimes the machine is able to resolve DNS queries through the local DNS server and sometimes it cannot.  I am also experiencing issues staying connected to the server via SSH (usually concurrent with a DNS resolution failure).  Here's a typical scenario...

1.  I reboot with "shutdown -r now" (the firewall is enabled as described above and the server is getting its IP from the DHCP server)
2.  I type "nslookup google.com" and receive back ";; connection timed out; no servers could be reached"
3.  I type "nslookup google.com" 10 minutes later, and it immediately gives an accurate reply.  But thenthe SSH session hangs and eventually ends.
4.  I try to reconnect immediately via SSH but the connection times out.
5.  I try to reconnect 15 minutes later via SSH and it lets me in.
6.  I type "nslookup google.com" and before it can give a reply the SSH session hangs and disconnects.

I'm getting similar problems (delays and time-outs) with commands like "netstat" and "iptables -L" which use DNS.  Sometimes these commands will work fine, but eventually they'll fail and I can't figure out what's causing the hit-and-miss results.  Rebooting fixes it sometimes, but not every time.

**Troubleshooting steps taken**

At first I thought it was a firewall problem because I only had port 53 open on UDP.  So, I opened it on TCP as well.  I also added UDP 22 because I only had it opened for TCP initially.  At first that seemed to fix it, but the problem returned later.

Currently, I have the firewall turned off.  I removed the */etc/network/if-pre-up.d/iptablesload* and */etc/network/if-post-down.d/iptablessave* files and the "iptables -L" now returns:

---------

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.122.0/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

---------

I believe the lines under FORWARD containing 192.168.122.0 were put there by the "virtual machine host" software that I chose during Ubuntu installation, but I can't be sure.  Also, "ps -aux" shows the following line:

---------

nobody    1009  0.0  0.0  21492   908 ?        S    15:25   0:00 dnsmasq --strict-order --bind-interfaces --pid-file=/var/run/libvirt/network/default.pid --conf-file=  --listen-address 192.168.122.1 --except-interface lo --dhcp-range 192.168.122.2,192.168.122.254 --dhcp-lease-max=253

---------

I'm guessing that was put there by the "virtual machine host" software, but again I'm not sure.

As I mentioned earlier, I had installed the system using a static IP, but later changed it.  I did this by modifying */etc/network/interfaces* to look like this:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp

I also removed the lines that I had added manually to */etc/resolv.conf*.  After doing this and rebooting, the machine got the correct DHCP addresses (the ones it has reserved by MAC) and the */etc/resolv.conf* file was populated correctly.  However, the DNS issues remain.

Before adding the TCP 53 and UDP 22 holes to my firewall, I was getting a lot of dropped packets.  I could see this in */var/log/messages* because iptables was logging all dropped packets.  Since adding those rules to the firewall iptables has not logged one single dropped packet (when it was turned on - it is currently turned off).  I thought this was a good sign, but it hasn't helped fix my DNS problem.

The only other output I can think to show is from the "/etc/inti.d/networking restart" command.  Here it is (obfuscated to hide IP/MAC/name information):

----------

There is already a pid file /var/run/dhclient.eth1.pid with pid 1165
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/--:--:--:cd:a2:59
Sending on   LPF/eth1/--:--:--:cd:a2:59
Sending on   Socket/fallback
DHCPRELEASE on eth1 to xxx.xxx.233.163 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 1131
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/--:--:--:cd:a2:5b
Sending on   LPF/eth0/--:--:--:cd:a2:5b
Sending on   Socket/fallback
DHCPRELEASE on eth0 to xxx.xxx.233.163 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/--:--:--:cd:a2:5b
Sending on   LPF/eth0/--:--:--:cd:a2:5b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPOFFER of xxx.xxx.99.79 from xxx.xxx.99.2
DHCPREQUEST of xxx.xxx.99.79 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of xxx.xxx.99.79 on eth0 to 255.255.255.255 port 67
DHCPACK of xxx.xxx.99.79 from xxx.xxx.99.2
bound to xxx.xxx.99.79 -- renewal in 130 seconds.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/--:--:--:cd:a2:59
Sending on   LPF/eth1/--:--:--:cd:a2:59
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPOFFER of xxx.xxx.99.78 from xxx.xxx.99.2
DHCPREQUEST of xxx.xxx.99.78 on eth1 to 255.255.255.255 port 67
DHCPACK of xxx.xxx.99.78 from xxx.xxx.99.2
bound to xxx.xxx.99.78 -- renewal in 32560 seconds.

-----------

You can see that the DHCP renewal takes some time - I don't know if that is due to the same issue that's causing the DNS problems or not.

So, that's all the information I can think to give.  Please let me know your suggestions for troubleshooting this.  Do you think it may be the "virtual machine host" software messing things up by running *dnsmasq*?  Did I misconfigure something when setting up the network interfaces?  Is it something else that I'm completely forgetting about?  Any and all tips are welcome.

Thanks in advance.

Dan

---

### Post by dcaunt on 2010-12-14
Just an update - apparently, problems arise when you put two NICs on the same subnet:

[http://ubuntuforums.org/showthread.php?t=566908](http://ubuntuforums.org/showthread.php?t=566908)

Luckily, the submitter of the linked thread found a solution.

-Dan

---

