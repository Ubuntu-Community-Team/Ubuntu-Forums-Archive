---
title: "Uncompicated Firewall and Gateway6"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by leetkrew on 2011-05-10
I share my network connection. If I enable UFW, my client computers can't open any ipv6 website. My client computers lost its IPv6 internet connectivity. I need my client computers to access ipv6 websites and services. 

**ufw disabled**
> 
C:\Documents and Settings\usr_testlab>ping ipv6.google.com

Pinging ipv6.l.google.com [2404:6800:8005::69] with 32 bytes of data:

Reply from 2404:6800:8005::69: time=476ms
Reply from 2404:6800:8005::69: time=471ms
Reply from 2404:6800:8005::69: time=465ms
Reply from 2404:6800:8005::69: time=466ms

Ping statistics for 2404:6800:8005::69:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 465ms, Maximum = 476ms, Average = 469ms

C:\Documents and Settings\usr_testlab>


**ufw enabled**
> 
C:\Documents and Settings\usr_testlab>ping ipv6.google.com

Pinging ipv6.l.google.com [2404:6800:8005::69] with 32 bytes of data:

Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 2404:6800:8005::69:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),

C:\Documents and Settings\usr_testlab>


**/etc/default/ufw**
> IPV6=yes

**/etc/gw6c/gw6c.conf**
> if_prefix=eth0

I am using Ubuntu 10.04. My server is behind the router. Please help, thanks

---

### Post by hazzey on 2011-06-11
I am writing to add that I am having this same problem.

A few quick details:

IPv6 enabled in /etc/default/ufw
IPv6 provided via freenet6/gogo6 tunnel.

Test steps:
Test ping6 ipv6.google.com - works from computer that is tunnel endpoint [server]
Test ping -6 ipv6.google.com - all time out when run from another computer on network.  These show up as blocked in the ufw.log

Change "sudo ufw default allow" - no change
Change "sudo ufw disable" - all ipv6 works from client computers.

I'll provide more details if needed, but to me this looks like an issue with the way that ufw handles IPv6.

Please note, all rules in "sudo ufw status" are "allow" type rules.  I have no issues with IPv4 connections.

---

