---
title: "NTP config for sync'ing local subnet (Ubuntu / Debian)"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by wolvesdread on 2011-02-22
Hi All

I'm trying to sync all servers on a subnet to a single machine.  The machines do not have access to the Internet.  I have Ubuntu 9.10 as the server and a bunch of Debian 5.04 boxes as the clients.  I need all the clients time to be sync'd to whatever I set the server time to be.

My current /etc/ntp.conf on the server (10.1.112.45)
# /etc/ntp.conf
driftfile /var/lib/ntp/ntp.drift
restrict 10.1.112.0 mask 255.255.255.0 nomodify notrap
restrict 127.0.0.1
broadcast 10.1.112.255

My current /etc/ntp.conf on the clients (10.1.112.*)
# /etc/ntp.conf
driftfile /var/lib/ntp/ntp.drift
server 10.1.112.45
restrict default notrust nomodify nopeer
restrict 10.1.112.45
restrict 127.0.0.1

I've issued /etc/init.d/ntp restart on both server and clients.  I've set the servers time to current time and the clients time to an earlier time manually with the "date -s xx:xx:xx" command.  The clients are not updating to the current time of the server.

I've Google'd my heart out and tried various suggested configurations to no avail.  I'm stymied.

When I run "ntpq -np" from one of the clients this is what I see.

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 10.1.112.45     .INIT.          16 u  174  512    0    0.000    0.000   0.000

From what I've read delay, offset and jitter should be non-zero values if this is working.

Is there anything obviously wrong here?  Suggestions appreciated.  I need to get this solved last week lol ;)  

THANKS!

---

