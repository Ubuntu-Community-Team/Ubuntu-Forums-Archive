---
title: "Script for pinging active connections?"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by Sastopher on 2009-01-18
I've got an old PC running ubuntu desktop working as our gateway/router for the house.  My roommates and I do a lot of online gaming, specifically Warcraft III which has somewhat outdated interface and doesn't show things like latency to host.

What I would like to do is, at the gateway level, scan active connections filtered by port number to determine the IP's people I'm connected to and send a ping to each one.  I have a rough idea about how to accomplish this but I'm having difficulty grabbing the important connections.  I've tried netstat but it only returns my ssh connection, rather than all the connections passing through it.  iftop will give me the connections in question, but I don't think I can pipe it to ping.  Can anyone suggest a means of accomplishing this?

Thank you so much!

---

### Post by Whizam on 2009-01-18
##Start Script##
```
#!/bin/bash

netstat -pant | grep [warcraft_port_number] | awk '{print $5}' > remote_hosts.tmp

exec < remote_hosts.tmp
while read host
do
ping $host
done

rm remote_hosts.tmp

```
##End Script##

You can have cron run that script every so often to ping the hosts.

The following line will run the script every 3 minutes
```
*/3 *   * * * [full path to above script]
```

Just make sure the script is executable.
You might have to do some more tweaking of the filtering of netstat in order to get the correct output of remote connections.

---

### Post by Sastopher on 2009-01-18
Thanks for the help, but netstat -pant doesn't give me a full list of active connections going through the gateway.  If I'm guessing right, it only tells me connections the gateway itself has made (such as ssh connections currently talking to it, or www connections if someone is browsing the internet from the gateway).  What it doesn't tell me is connections other computers on the LAN have initiated.

```
sastopher@Sasto-router:~/Documents$ netstat -pant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      12951/perl
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      4965/cupsd
tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN      30879/5
tcp6       0      0 :::22                   :::*                    LISTEN      4905/sshd
tcp6       0      0 ::1:6010                :::*                    LISTEN      30879/5
tcp6       0    296 192.168.1.1:22          192.168.1.100:59144     ESTABLISHED 30876/sshd: sastoph

```
(running through sudo doesn't give me any more information)

I can't seem to get this information through any use of netstat and various flags.  I know it's possible to grab this info since I use iftop to get it all the time, but iftop uses a continuously updating console display and can't be piped out as far as I know.  I've also tried using watch with netstat and checking other types of connections that are streaming to make sure I'm not missing anything, but no luck so far.  Additionally, netstat on the Vista PC I'm playing the game from gives me the missing connections.

---

### Post by Sastopher on 2009-01-18
I fixed my problem by installing netstat-nat, which gives NATed connections.  Thanks again Whizam for providing me with the rest.  I'll use your script as an example and learn from it.  Thanks a ton!

---

