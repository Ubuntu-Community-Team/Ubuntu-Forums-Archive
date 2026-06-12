---
title: "Trying to setup dhcp/tftp to pxe boot an Alix sbc"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by dazz100 on 2012-10-14
Hello

I am trying to install IPCop on an Alix sbc.  To do that I need to setup a laptop to act as a dhcp server.  The Alix doesn't seem to be talking with the laptop dhcp server.   It appears that the eth0 doesn't seem to be setting up properly.   I don't know enough about Ubuntu to know how to fix this problem.  I am seeking advice on where to look next.

The laptop and Alix sbc are plugged into an ethernet switch.  Nothing else is connected.  The wifi link on the laptop was switched off before trying to pxe boot the Alix.  The laptop is set up for static ip addresses but I don't think that should affect the operation of the dhcp server.

The ethernet status is shown below:
 
```
darren@toshiba:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:b7:f9:b2:55  
          inet6 addr: fe80::215:b7ff:fef9:b255/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5346 (5.3 KB)  TX bytes:73251 (73.2 KB)
          Interrupt:16 Memory:ffde0000-ffe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26239 (26.2 KB)  TX bytes:26239 (26.2 KB)

```

I have installed dhcp3 (isc-dhcp-server) and tftp OK.
Below is the dhcp.conf file.  Most is copied from someone elses work  and I have modified the required parameters (eg. client address)

```

# Configuration file for ISC dhcpd for Debian
# Modified for pxe boot of Alix sbc
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#
option domain-name "home";

default-lease-time 600;
max-lease-time 7200;

authoritative;
allow booting;
allow bootp;

# The next paragraph needs to be modified to fit your case
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.200 192.168.1.210;
  option broadcast-address 192.168.1.255;
# the gateway address which can be different
# (access to the internet for instance)
  option routers 192.168.1.2;
# indicate the dns you want to use
  option domain-name-servers 192.168.1.3;
}

group {
  next-server 192.168.1.3;
  host tftpclient {
# tftp client hardware address
  hardware ethernet  00:0D:B9:24:D6:9C;
#  filename "/pxelinux.0";
#   filename "/tftpboot/pxelinux.0";
      filename "pxelinix.0";
 }
}

```

The sys.log shows:

```
darren@toshiba:~$ sudo tail /var/log/syslog
Oct 14 22:20:21 toshiba NetworkManager[736]: <warn> Activation (eth0) failed.
Oct 14 22:20:21 toshiba NetworkManager[736]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct 14 22:20:21 toshiba NetworkManager[736]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct 14 22:20:21 toshiba NetworkManager[736]: <info> (eth0): deactivating device (reason 'none') [0]
Oct 14 22:20:21 toshiba avahi-daemon[763]: Withdrawing address record for fe80::215:b7ff:fef9:b255 on eth0.
Oct 14 22:20:21 toshiba avahi-daemon[763]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::215:b7ff:fef9:b255.
Oct 14 22:20:21 toshiba avahi-daemon[763]: Interface eth0.IPv6 no longer relevant for mDNS.
Oct 14 22:20:23 toshiba avahi-daemon[763]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::215:b7ff:fef9:b255.
Oct 14 22:20:23 toshiba avahi-daemon[763]: New relevant interface eth0.IPv6 for mDNS.
Oct 14 22:20:23 toshiba avahi-daemon[763]: Registering new address record for fe80::215:b7ff:fef9:b255 on eth0.*.

```

Any pointers to where I should start looking for a solution would be much appreciated.

---

