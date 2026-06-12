---
title: "Slow transfer with a Broadcom BCM5722 on 12.10"
date: 2012-11-17
forum: Networking &amp; Wireless
---

### Post by ol1v3r on 2012-11-17
Hi everyone,

I'm having a really strange issue with network transfers on my Ubuntu 12.10 installation.

I have a SAMBA server running, which serves large files to it's clients. The downloading of files from the server is fine (10MBps), but when clients try to upload to the server, the transfer speed usually sits around the 100Kbps mark. The same rates apply for SFTP transfers, too. 

I've also found this rate limit happens when downloading files via the internet on the installation, hitting the same 100Kbps mark using wget or apt. I find however, that SABNZBd seems to download absolutely fine from the internet, maxing out the connection at 2.2MBps.

The full listing from lspci is:
> 11:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express

Ethtool outputs:

> driver: tg3
version: 3.123
firmware-version: 5722-v3.07, ASFIPMI v6.02
bus-info: 0000:11:00.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: no

I have also noticed that the card is hitting a lot of packet errors in ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:1f:29:eb:32:7c  
          inet addr:192.168.1.144  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:191391 errors:19664 dropped:0 overruns:0 frame:18466
          TX packets:175703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:219279790 (219.2 MB)  TX bytes:44799558 (44.7 MB)
          Interrupt:18 

I have changed the cabling and the port it uses on the router to troubleshoot this.

I have been suggested to use the following in my /etc/sysctl.conf. Which has not made a difference for this situation:

> net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1
vm.swappiness = 10

I have also tried to compile Broadcom drivers from their website for my card, but 'make' generated the following:
> /home/oliver/Server/Linux/Driver/tg3-3.124c/tg3.c:96:24: fatal error: asm/system.h: No such file or directory


Finally, I had also disabled UFW which had no change on the transfer rate.

Does anyone have any ideas? I'm really stumped on this one! I have a feeling it's the card/driver at fault here, but I can't think of what else I could do apart from buy a new one!

Thanks,
Oli

---

### Post by ol1v3r on 2012-11-17
It looks like the high number of frame errors might be to blame for this. Any ideas what could be causing it?

---

### Post by urix on 2012-11-26
The next logical step would be to change the card, try a different flavour/brand… the troubleshooting steps you have taken so far are fairly comprehensive.  If the same issue persists post up the outputs so they can be compared, however this looks more like a hardware issue than anything else.

---

