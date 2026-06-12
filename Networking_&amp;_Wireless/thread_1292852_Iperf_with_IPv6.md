---
title: "Iperf with IPv6"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by MelanieS on 2009-10-16
Hello!

 I'm now on trying Iperf within Ubuntu by using 2 motes where the transmission should be with IPv6. 

At the server I have: iperf -s -V
At the client I have: iperf -c fe80::7600:12ff:fee6:6c8e -V

But then I get:
connect failed: Invalid argument
write1 failed: Broken pipe
write2 failed: Broken pipe
------------------------------------------------------------
Client connecting to fe80::7600:12ff:fee6:6c8e, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local :: port 0 connected with fe80::7600:12ff:fee6:6c8e port 5001
[  3]  0.0- 0.0 sec  0.00 Bytes  0.00 bits/sec

What could be the problem? Thanks for any help
[COLOR=#888888]Melanie[/COLOR]

---

### Post by jonobr on 2009-10-16
Hello


And welcome to the forums,

AFAIK I remember reading that Iperf with IPV6 from the repos has a bug in it that it cant set the client socket correctly.

There was a patch released to fix this, Ill take a look in launchpad, but this is not hitting the major headlines due to the amount of IPV6 Ubuntu clients and those that use it with Iperf.


Ill check back with you later after doing a bit of looking around

---

