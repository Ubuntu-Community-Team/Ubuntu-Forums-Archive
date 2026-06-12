---
title: "Home Network"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by Coyote007 on 2011-07-13
Good morning.

I had a FreeBSD server as my router/firewall for my home network. After  many many years of great service, it finally died a couple of days ago  *sniff*

I am attempting to duplicate that setup using my natty-64 workstation.  But after searching these forums and the interweb the past few days, I  am unable to get this working. Here is a diagram of my bsd setup and what I want to  accomplish with natty:

```

[FONT=Courier New]ISP(cable) --- eth0(dhcp)
               eth1(static) --- switch --- workstation-1(static)
                                       --- workstation-n(static)
                                       --- wap --- laptops(static)
[/FONT]
```I will obviously need NAT between my eth1 private ip assignments and eth0. I do not have any iptable rules defined - I will add them later once I can connect.

I am not that experienced with networking, so any advice or pointing me in the right direction is greatly appreciated.

Thank you for your help!

---

### Post by ratcheer on 2011-07-13
A quick Google search found this. I hope it helps.

[http://www.server-servers.com/ubuntu-router-network-gateway/](http://www.server-servers.com/ubuntu-router-network-gateway/)

Tim

---

### Post by Coyote007 on 2011-07-13
Thanks for the link, Tim.

The article, along with the others I read, wants to install a dhcp server. I only want manually assigned static ips for my internal network. Do I have to forego the static assignments and use dhcp internally in order to get this configuration to work?

Thanks again.

---

### Post by ratcheer on 2011-07-13
I have no idea, I have never done it. I just found you some guidance on the subject you were asking about.

However, in the near future, I plan on doing a similar thing on a dedicated machine running either pfSense or Untangled.

Tim

---

### Post by Coyote007 on 2011-07-13
I appreciate your help, Tim.

The reason I asked is that my workstation is my development box. I keep things very simple and clean. I am not fond if having any software arbitrarily configure things, however minor, on my system that I am not personally controlling. 

I also have the other computers and peripheral devices statically set to control access. For example, the 10.5.2.1x range is where all of my wife's computers are attached, the 10.5.2.2x is for my daughter's devices, etc. Based on this, I can prevent my daughter from accidentally writing to e.g. my plotter.

Does anyone know if it is necessary to install and configure dhcp for the internal network to function properly?

---

### Post by ratcheer on 2011-07-13
Giving it some thought (but again, I have never actually done it myself), I see no reason why you could not assign static IP's to your LAN hosts, whether or not you were running DHCP. So, I say you should try it without DHCP and see what happens.

Tim

---

### Post by Coyote007 on 2011-07-13
Hi Tim,

Yes, I had tried the procedures listed in many of the articles without success. However, this morning I removed all previous changes and rebooted to ensure they were cleared. I double checked interfaces, iptables, etc. All were set to default.

The following procedure works for my setup, in case anyone else had the same issue.

And for Chilli's reference, as stated in another article, IT WORKS! :)

Step 1.
Edit the /etc/network/interfaces file as follows:
```

auto lo
iface lo inet loopback

# WAN
auto eth0
iface eth0 inet dhcp
# iptable save/load goes here.

# LAN
auto eth1
iface eth1 inet static
address 10.5.2.99
netmask 255.255.255.0
network 10.5.2.0
broadcast 10.5.2.255

```Step 2. Edit /etc/sysctl.conf as follows. Note the two appended lines at EOF.
```

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

```Step 3. Restart the network.

```

sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                              ssh stop/waiting
ssh start/running, process 1837
ssh stop/waiting
ssh start/running, process 1893

```Step 4. Create/Edit iptables as desired. See [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo). Specifically, the Configuration on Startup section, Solution #1.
```

sudo iptables -L 
Chain INPUT (policy ACCEPT) 
target     prot opt source               destination 

Chain FORWARD (policy ACCEPT) 
target     prot opt source               destination 
ACCEPT     all  --  10.5.2.0/24          anywhere            ctstate NEW 
ACCEPT     all  --  anywhere             anywhere            ctstate  RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT) 
target     prot opt source               destination 

```Note the addition of the iptable rules lines to your /etc/networkings/interfaces file explained in the howto article that I referenced in Step 1.

This prcedure works for me. I can now connect from all machines through the gateway to the interweb using Natty-64bit, dual NICs, DHCP and Static IPs.

...now for the enjoyable task of learning iptabels!

Thank you, Tim, for your help!

---

