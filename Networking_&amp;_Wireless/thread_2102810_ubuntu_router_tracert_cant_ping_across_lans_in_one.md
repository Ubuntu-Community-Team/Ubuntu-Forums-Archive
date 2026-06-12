---
title: "ubuntu router tracert cant ping across lans in one direction other ok"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-08
I have ubuntu router questions.
you can see tracert can complete on way but not other way.
How to make that work?

This way from second win7 works to first win7
```
C:\Users\scott>tracert 192.168.200.36

Tracing route to WIN7 [192.168.200.36]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  SCOTT-P5QC [10.42.0.1]
  2    <1 ms    <1 ms    <1 ms  wr850g.hr.cox.net [192.168.1.1]
  3    25 ms    24 ms    31 ms  WIN7 [192.168.1.100]
  4    18 ms    17 ms    40 ms  WIN7 [192.168.200.36]

Trace complete.

C:\Users\scott>

```


This way from first win7 to second win7 broken
```

C:\Users\scott>tracert 10.42.0.19

Tracing route to 10.42.0.19 over a maximum of 30 hops

  1    52 ms     1 ms     1 ms  hubrouter.westell.com [192.168.200.1]
  2    43 ms    98 ms    45 ms  192.168.1.1
  3    45 ms   105 ms    24 ms  SCOTT-PC [192.168.1.102]
  4  SCOTT-PC [192.168.1.102]  reports: Destination protocol unreachable.

Trace complete.

```

From first win7 to ubuntu router works
```

C:\Users\scott>tracert 10.42.0.1

Tracing route to SCOTT-P5QC [10.42.0.1]
over a maximum of 30 hops:

  1   105 ms    <1 ms     4 ms  hubrouter.westell.com [192.168.200.1]
  2    19 ms    17 ms    33 ms  192.168.1.1
  3    35 ms    34 ms     5 ms  SCOTT-P5QC [10.42.0.1]

Trace complete.

C:\Users\scott>


```

netstat routes in ubuntu router
```

scott@scott-P5QC:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         wr850g.hr.cox.n 0.0.0.0         UG        0 0          0 eth2
10.42.0.0       *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
192.168.1.0     *               255.255.255.0   U         0 0          0 eth2
scott@scott-P5QC:~$ 

```

hand copy of lan layout

[IMG]https://lh5.googleusercontent.com/-uChF5IIApj8/UOrFVvJYMiI/AAAAAAAAEV0/lyAJAvYks9k/s1024/lan.jpeg[/IMG]

---

### Post by sdowney717 on 2013-01-08
Solved by installing webmin!!

I did get a certificate warning, log in anyway!

after you log in to webmin then on left side click
Networking then Linux firewall.

I got a message saying 2 rules had been entered that webmin could not deal with, so saved current iptables to a file.

The I reset the firewall.
And it worked, I can browse shared folders on all the computers. On first win7 pc, I have to map network drive since it is in a different subnet.

The webmin shows a very nice gui to the firewall configuration!


[IMG]https://lh4.googleusercontent.com/-JLN674cmEuc/UOx_lsKNoNI/AAAAAAAAEXo/GtGZ8LHzexA/s1440/fixedfirewall.png[/IMG]

---

### Post by jsuiker on 2013-03-20
I've only got the server version of Ubuntu, so I can't install webmin (I think) In any case, I'd rather just get my iptables configured properly.  Can you do a printout of what yours are?  IPTABLES, NAT, etc...

---

