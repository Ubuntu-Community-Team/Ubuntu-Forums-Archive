---
title: "Network Connections Refused"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by GrumpyBum on 2013-06-13
Hi All,

I am troubleshooting a server at the moment but I also wanted to ask if anyone may have a quick solution to this.

Basically, the server is rejecting all connections to port 3306 no matter is I am using PuTTY or a direct MySQL connection.
This is happening both with the firewall (ufw) turned on or off and I can confirm that the server is listening on this port.

If anyone can provide some insight this would be great, please let me know if additional information is required.

The quick facts, Ubuntu 12.04.2 LTS / 3.5.0-23 x86 Header.
And now the other facts,

[IMG]http://jaradsc.co.nz/temp/portinfoms.PNG[/IMG]

[IMG]http://jaradsc.co.nz/temp/lesshostsa.PNG[/IMG]

And a DUMP of the iptables,

> tylerdurden@APIDCMYSQL:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
ufw-before-logging-input  all  --  anywhere             anywhere
ufw-before-input  all  --  anywhere             anywhere
ufw-after-input  all  --  anywhere             anywhere
ufw-after-logging-input  all  --  anywhere             anywhere
ufw-reject-input  all  --  anywhere             anywhere
ufw-track-input  all  --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:mysql


Chain FORWARD (policy DROP)
target     prot opt source               destination
ufw-before-logging-forward  all  --  anywhere             anywhere
ufw-before-forward  all  --  anywhere             anywhere
ufw-after-forward  all  --  anywhere             anywhere
ufw-after-logging-forward  all  --  anywhere             anywhere
ufw-reject-forward  all  --  anywhere             anywhere


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ufw-before-logging-output  all  --  anywhere             anywhere
ufw-before-output  all  --  anywhere             anywhere
ufw-after-output  all  --  anywhere             anywhere
ufw-after-logging-output  all  --  anywhere             anywhere
ufw-reject-output  all  --  anywhere             anywhere
ufw-track-output  all  --  anywhere             anywhere


Chain ufw-after-forward (1 references)
target     prot opt source               destination


Chain ufw-after-input (1 references)
target     prot opt source               destination
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
target     prot opt source               destination


Chain ufw-after-output (1 references)
target     prot opt source               destination


Chain ufw-before-forward (1 references)
target     prot opt source               destination
ufw-user-forward  all  --  anywhere             anywhere


Chain ufw-before-input (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             state INVALID
DROP       all  --  anywhere             anywhere             state INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere


Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination


Chain ufw-before-logging-input (1 references)
target     prot opt source               destination


Chain ufw-before-logging-output (1 references)
target     prot opt source               destination


Chain ufw-before-output (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere


Chain ufw-logging-allow (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             state INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere


Chain ufw-reject-forward (1 references)
target     prot opt source               destination


Chain ufw-reject-input (1 references)
target     prot opt source               destination


Chain ufw-reject-output (1 references)
target     prot opt source               destination


Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere


Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere


Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain ufw-track-input (1 references)
target     prot opt source               destination


Chain ufw-track-output (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             state NEW
ACCEPT     udp  --  anywhere             anywhere             state NEW


Chain ufw-user-forward (1 references)
target     prot opt source               destination


Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     udp  --  anywhere             anywhere             udp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:mysql
ACCEPT     udp  --  anywhere             anywhere             udp dpt:mysql
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     udp  --  anywhere             anywhere             udp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere             udp dpt:ssh


Chain ufw-user-limit (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination


Chain ufw-user-logging-input (0 references)
target     prot opt source               destination


Chain ufw-user-logging-output (0 references)
target     prot opt source               destination


Chain ufw-user-output (1 references)
target     prot opt source               destination
tylerdurden@APIDCMYSQL:~$




Thanks all, have a great day.

---

### Post by SeijiSensei on 2013-06-13
Well, first, are you sure that mysqld is running on the remote machine?  You might also need to check and see whether it is constrained to use only localhost (127.0.0.1) by default.  Can you telnet to localhost:3306 on the machine itself, but not to external_interface:3306 from a remote machine?

---

### Post by GrumpyBum on 2013-06-13
Hello,

You would be correct, localhost telnet is fine but not from other locations.

[IMG]http://jaradsc.co.nz/temp/telnet.PNG[/IMG]


But you have made me think about other possible issues,
I have just muted 'skip-external-locking' in in my.cnf and changed 'bind-address' to the server IP and this was set as a loop back address.

I have restarted the mysql service and this looks to be resolved.
Testing further and will happily update on the outcome.

Thanks,

---

### Post by GrumpyBum on 2013-06-13
And we have lift off, Thanks [[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195")[COLOR=#000000][/COLOR]

---

