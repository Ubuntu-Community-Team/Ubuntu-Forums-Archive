---
title: "TFTP Very Slow"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by ddjones on 2011-10-12
I recently upgraded systems from Ubuntu 10.04 on a Core2 Quad to 11.04 on an i7. After setting everything up, I noticed I was having issues with tftp.

I apt-get installed: xinetd tftpd tftp

I created /etc/xinetd.d/tftp with the following:

service tftp
{
protocol        = udp
port            = 69
socket_type     = dgram
wait            = yes
user            = nobody
server          = /usr/sbin/in.tftpd
server_args     = /tftpboot
disable         = no
}


But tftp get from another machine to the new one is running extremely slow - around 1,442B/second. For comparison, on my old machine, tftp gets would run at about 1,000,000B/second, so there is an order of magnitude in the hundreds difference. I use tftp to load a 3 MB image on another system and it used to take 3 seconds and now takes 30 minutes!

I'm at a loss for what could possibly be the issue and what to do and any help would be very much appreciated. Thanks!

---

### Post by ddjones on 2011-10-12
Some more debugging information:

I've tested downloaded speeds and they're through the roof, so it seems to be something innately tied to tftp and not networking as a whole.


Also, checking "netstat -a | grep tftp" does return the expected "udp 0 0 *:tftp" but again, it takes about 15 seconds while on my other system it's instantaneous.

---

### Post by DavidA2011 on 2013-01-17
Hi
 
Did you find the reason for this?  tftp was fine in Ubuntu 10.04LTS for me, but is very slow in Ubuntu 12.04LTS.
 
David

---

### Post by jonobr on 2013-01-17
Maybe if you try using FTP or some other transfer protocol , you could check if this is related specifically to TFTP or if this is a problem with file transfers in general.

If your hardcore, you could try using iperf to get some BW measurements and compare UDP versus TCP
(TFTP uses UDP, FTP uses TFTP)

If its more of a general problem maybe installing and using [ethtool]("http://manpages.ubuntu.com/manpages/hardy/man8/ethtool.8.html") may help you see if there is something up with the interface.

---

