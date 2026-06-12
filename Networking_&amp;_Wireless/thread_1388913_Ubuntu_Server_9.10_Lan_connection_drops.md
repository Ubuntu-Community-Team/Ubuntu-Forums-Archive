---
title: "Ubuntu Server 9.10 Lan connection drops"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by bot2k9 on 2010-01-23
Hello,

I got a new low power file server (Atom 330 with ion), but didn't enjoy it since.

I installed Ubuntu server 9.10 64bit.

I randomly experience connection drops. As I'm installing and testing, there are lots of ssh windows open, I transfer much data using scp from my laptop to the server (all connected to wired lan).

Connection drops are as follows: ssh windows terminate with "connection reset by peer", but not always all the ssh windows terminate. For example, I edited a mediatomb config using nano, that stayed open even with scp and all other ssh windows cut.

I also have apache2 installed because I'm running urd (a usenet download tool). It seems that when I start the deamon, connection drops. So I killed apache2 to try out but that didn't solve the problem.

I left ping run all the time, and the server is pinging back all the time, which is really strange as I thought that a connection drop means the whole network interface going down.

When this drop occurs, I have to wait 2 minutes until I can ssh back into the server.

I also installed mediatomb, but it isn't really fun to stream a video to my ps3 as it always hangs after 5 to 10 minutes.


What info do you need?

Anyone an idea how to solve this?
Thanks in advance

```
lspci:
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)

``````
xxxxx@homeserver:~$ tail -F /var/log/syslog
Jan 23 23:09:04 homeserver kernel: [   10.044775] type=1503 audit(1264284544.104:16): operation="open" pid=1002 parent=1001 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 23 23:09:04 homeserver /etc/mysql/debian-start[1013]: Upgrading MySQL tables if necessary.
Jan 23 23:09:04 homeserver /etc/mysql/debian-start[1017]: Looking for 'mysql' as: /usr/bin/mysql
Jan 23 23:09:04 homeserver /etc/mysql/debian-start[1017]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Jan 23 23:09:04 homeserver /etc/mysql/debian-start[1017]: This installation of MySQL is already upgraded to 5.1.37, use --force if you still need to run mysql_upgrade
Jan 23 23:09:04 homeserver /etc/mysql/debian-start[1039]: Checking for insecure root accounts.
Jan 23 23:09:04 homeserver /etc/mysql/debian-start[1052]: Triggering myisam-recover for all MyISAM tables
Jan 23 23:09:09 homeserver kernel: [   15.600015] eth0: no IPv6 routers present
Jan 23 23:17:02 homeserver CRON[1555]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 23 23:39:01 homeserver CRON[2017]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan 24 00:09:01 homeserver CRON[2300]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan 24 00:17:01 homeserver CRON[2379]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

---

### Post by bot2k9 on 2010-01-25
I just installed ubuntu server 8.04, just to test if the problem still is there, and oh wonder, it's just exactly the same case. 

An idea anyone? 

I installed mediatomb and streamed a video, and it just quits playing after 5-10 minutes. After that, I have to wait about 1 minute and I can just resume playing. But sometimes, if I ssh into the server, it stops and doesn't come back at all, ping to the server being fine. Only a restart helps. 

Greetings

---

### Post by bot2k9 on 2010-01-26
[Solved]  I just found out that my brother set up his xbox to have the same ip, so everytime he tried to get online, I had a disconnect.  The whole thing now runs like a charm.  Greetings

---

### Post by sarraceno on 2010-02-05
Ok, I suspect of samething like you had but in diferent way.

Pls, anyone, read [http://ubuntuforums.org/showthread.php?t=1399032](http://ubuntuforums.org/showthread.php?t=1399032)

I believe that I have in my office lan some host jammed or trojaned which may submit some bad packets or some packets with my IP and provide collision. What I do not understand is why Windows doesn't get equal Beauvoir.

Any strategy to deal with this?

Thanks all!

---

