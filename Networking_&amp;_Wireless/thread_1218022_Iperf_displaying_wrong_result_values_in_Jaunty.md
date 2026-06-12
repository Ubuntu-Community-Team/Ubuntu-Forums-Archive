---
title: "Iperf displaying wrong result values in Jaunty"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by Annihilist on 2009-07-20
Hi,

I recently moved house and got a new nice and fast internet connection. I am wanting to measure the speed I get between my laptop running Jaunty (I am in NZ), and a server I rent in America running Lenny. I installed iperf on both machines and ran the following commands.

Server (machine in America):
```

iperf -s -p 7777 -w 2M
------------------------------------------------------------
Server listening on TCP port 7777
TCP window size:   256 KByte (WARNING: requested 2.00 MByte)
------------------------------------------------------------

```

Client (laptop in NZ):
```

iperf -c driven-monkey.com -p 7777 -fM -w 2M -i 1
------------------------------------------------------------
Client connecting to driven-monkey.com, TCP port 7777
TCP window size: 0.25 MByte (WARNING: requested 2.00 MByte)
------------------------------------------------------------
[  3] local 192.168.1.64 port 59602 connected with 216.32.68.237 port 7777

```

The results I am getting seem a little high to me...
```

[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 1.0 sec  0.16 MBytes  0.16 MBytes/sec
[  3]  1.0- 2.0 sec  17592186044416 MBytes  17592186044416 MBytes/sec
[  3]  2.0- 3.0 sec  17592186044416 MBytes  17592186044416 MBytes/sec
[  3]  3.0- 4.0 sec  17592186044416 MBytes  17592186044416 MBytes/sec
[  3]  4.0- 5.0 sec  17592186044416 MBytes  17592186044416 MBytes/sec
[  3]  5.0- 6.0 sec  17592186044416 MBytes  17592186044416 MBytes/sec
[  3]  6.0- 7.0 sec  17592186044416 MBytes  17592186044416 MBytes/sec
[  3]  7.0- 8.0 sec  17592186044416 MBytes  17592186044416 MBytes/sec
[  3]  8.0- 9.0 sec  17592186044416 MBytes  17592186044416 MBytes/sec
[  3]  0.0-10.0 sec  17592186044416 MBytes  1758143148278 MBytes/sec

```

Any ideas? I read about an overflow error that can cause this but the only solution was to install the latest version. I only just installed it off apt tonight so I dont think that is the issue.

---

