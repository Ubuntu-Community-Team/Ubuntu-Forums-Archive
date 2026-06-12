---
title: "Why are ports open after install?"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by Hadeda on 2009-11-01
[SIZE=2]I do not understand the data Network Tools show me and would appreciate some help :)

Quote
[/SIZE][INDENT][SIZE=2] "Ubuntu install opens zero ports to the outside world, so a firewall is redundant. However, installing "server software" will cause ports to open" [/SIZE]
[/INDENT][SIZE=2]Unquote.
[/SIZE][INDENT][SIZE=2](From:  [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421) )[/SIZE]
[/INDENT][SIZE=2]
I don't know of any server software. It's a default/ brand new installation of 9.04. Therefore **my questions are**:

1) Why are ports open? (see below)
2) Why is there a  0.0.0.0 gateway address?
3) Why is there a 169.254.0.0 address that the computer is connected to after a default / no update install of 9.04 ?

*Some data:*

The computer is connected to a D-Link router.
DHCP (auto) did not work - had to do manual configure (IP, gateway, mask).

**Network Tools** check reveals:
[/SIZE][INDENT][SIZE=2]1) PortScan: Ports 51503 and 8088 (and 80) is open to "unknown" (no browser window is open, the port number changes but stays in the 50xxx range). [/SIZE]
[SIZE=2]2) Active network:    udp    0.0.0.0   35679    and   udp    0.0.0.0     5353[/SIZE]
[SIZE=2]3) Routing: 169.254.0.0    0.0.0.0    255.255.0.0 (which is not the computer's IP address/ gateway/mask).[/SIZE]
[/INDENT][SIZE=2]Is there a simple explanation?
Many thanks![/SIZE]

---

### Post by Groodles on 2009-11-01
> **Hadeda said:**
> [SIZE=2]I do not understand the data Network Tools show me and would appreciate some help :)

Quote
[/SIZE][INDENT][SIZE=2] "Ubuntu install opens zero ports to the outside world, so a firewall is redundant. However, installing "server software" will cause ports to open" [/SIZE]
[/INDENT][SIZE=2]Unquote.
[/SIZE][INDENT][SIZE=2](From:  [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421) )[/SIZE]
[/INDENT][SIZE=2]
I don't know of any server software. It's a default/ brand new installation of 9.04. Therefore **my questions are**:

1) Why are ports open? (see below)
2) Why is there a  0.0.0.0 gateway address?
3) Why is there a 169.254.0.0 address that the computer is connected to after a default / no update install of 9.04 ?

*Some data:*

The computer is connected to a D-Link router.
DHCP (auto) did not work - had to do manual configure (IP, gateway, mask).

**Network Tools** check reveals:
[/SIZE][INDENT][SIZE=2]1) PortScan: Ports 51503 and 8088 (and 80) is open to "unknown" (no browser window is open, the port number changes but stays in the 50xxx range). [/SIZE]
[SIZE=2]2) Active network:    udp    0.0.0.0   35679    and   udp    0.0.0.0     5353[/SIZE]
[SIZE=2]3) Routing: 169.254.0.0    0.0.0.0    255.255.0.0 (which is not the computer's IP address/ gateway/mask).[/SIZE]
[/INDENT][SIZE=2]Is there a simple explanation?
Many thanks![/SIZE]

If you configure for DHCP and the machine fails to contact a DHCP server, it will eventually timeout and assign itself an IP address in the 169.254.x.x range.  The routing you have described is a result of the self assignment.

Port 80 is open.  Did you install apache?

Run the following command, it'll tell you what services are running that have ports open.

```


sudo netstat -tulp


```

---

### Post by Hadeda on 2009-11-02
Great help, thanks Groodles.

No, I did not install apache.

*sudo netstat -tulp*  returns:
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:ipp           *:*                     LISTEN      2689/cupsd      
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      2689/cupsd      
udp        0      0 *:34910                 *:*                                 2664/avahi-daemon: 
udp        0      0 *:mdns                  *:*                                 2664/avahi-daemon: 

Yahoo: "Avahi is a fully LGPL framework for Multicast DNS Service Discovery".

I managed to get the DHCP auto mode to work, but the results in netstat are the same. :-(

Does this help to shed some light onto the solution?

Many thanks!

---

