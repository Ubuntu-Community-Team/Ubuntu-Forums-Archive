---
title: "No TV with Internet.  gigantic syslog"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by kflorek on 2011-09-20
running 64 bit Ubuntu natty on an AMD 6 core processor.

I am currently getting, at the rate of 5 per second, lines identical to this (except for time), in my /var/log/syslog

Sep 20 09:54:16 ma78-u17 kernel: [80684.300613] Inbound IN=eth0 OUT= MAC=00:1f:d0:9c:f9:09:00:18:dd:01:b9:fe:08:00 SRC=192.168.0.52 DST=192.168.0.1 LEN=1356 TOS=0x00 PREC=0x00 TTL=2 ID=19989 DF PROTO=UDP SPT=5004 DPT=52384 LEN=1336 

SRC=192.168.0.52 means this is from my network TV tuner, an hdhomerun. I presume the hdhomerun is sending something.

While I'm connected to the Internet, as I am now, I can't access the hdhomerun. Nothing. It is not detected. But pinging gets a response time.  As soon as I disconnect (I have dialup Internet), the hdhomerun is back. I would like to fix this. I figure the errors and the missing hdhomerun are connected.

 What is putting these error(?) messages in the syslog? How can I figure that out?

 What is blocking the hdhomerun when I dial-up? avahi? NetworkManager? dnsmasq? How can I track it down? What can I change?

 There is no firewall running according to System Monitor, at least not ufw or firestarter. Will iptables do something which blocks ip's even with no firewall running?

 There are dhcp leases being written, according to the syslog, to the hdhomerun, but some or all may be be old.

There is no router Just my other computers (which have been off for several days) and the hdhomerun are connected to the network interface through a switch.

---beginning of lease file

# The format of this file is documented in the dhcpd.leases(5) manual page.
# This lease file was written by isc-dhcp-4.1.1-P1

lease 192.168.0.63 {
  starts 2 2011/09/13 22:18:46;
  ends 2 2011/09/13 22:28:46;
  tstp 2 2011/09/13 22:28:46;
  cltt 2 2011/09/13 22:18:46;
  binding state free;
  hardware ethernet 00:18:dd:01:b9:fe;
  uid "\001\000\030\335\001\271\376";
}
lease 192.168.0.13 {
  starts 5 2011/09/16 04:35:37;
  ends 5 2011/09/16 06:35:37;
  tstp 5 2011/09/16 06:35:37;
  cltt 5 2011/09/16 04:35:37;
  binding state free;
  hardware ethernet 00:18:dd:01:b9:fe;
  uid "\001\000\030\335\001\271\376";
}
lease 192.168.0.52 {
  starts 2 2011/09/20 16:31:24;
  ends 2 2011/09/20 18:31:24;
  cltt 2 2011/09/20 16:31:24;
  binding state active;
  next binding state free;
  hardware ethernet 00:18:dd:01:b9:fe;
  uid "\001\000\030\335\001\271\376";
  client-hostname "HDHR-101B9FE8";
}
server-duid "\000\001\000\001\025\362i\334\000\037\320\234\371\011";

---end of lease file

For some unknown reason, the last lease starts in the future. The current time is 13:09 by the tray clock, which is before 16:31.

 Believe me, I have tried many FAQs and HOWTO's over the last few weeks, but this guessing approach has gotten nowhere.

---

