---
title: "Wireless Internet Slower than Usual."
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by PhazzedOut on 2009-06-27
My max Internet download speed is 165kpbs, that is the speed I get when I download on Vista. On Ubuntu 9.04 64-bit slows and sometimes disconnects my Internet. I think I narrowed down the problem to some possibilities.  I noticed that when I use the Internet at the house of my girlfriend my speed on Ubuntu is the same on Vista, but her wireless router is those AT&T 2Wire ones. My wireless router is a NetGear one I got to make my modem a router. I think it might be driver issues or Ubuntu is not working well with IPv6, but idk I am not much of a Linux expert quite yet. If there is a fix to this can someone tell me. 

Thank You.

---

### Post by Brandon Williams on 2009-06-27
Some older network hardware has trouble with large TCP window scale settings. With 165kbps, you don't need window scaling, so try disabling it to see if that helps: sudo sysctl -w net.ipv4.tcp_window_scaling=0

If that helps, you can add this setting to /etc/sysctl.conf to enable it every time you start the computer.

---

### Post by philcamlin on 2009-06-27
go to 

[http://www.speedtest.net/](http://www.speedtest.net/)

whats your speed? :popcorn:

to show the difference

---

### Post by PhazzedOut on 2009-06-29
Oh my speed given by my ISP is 1.5mbps. Well it works on and off. Today it goes up to 10kbps but yesterday it was going at the usual speed of 160kbps

---

### Post by superprash2003 on 2009-06-30
you mean 10mbps?

---

