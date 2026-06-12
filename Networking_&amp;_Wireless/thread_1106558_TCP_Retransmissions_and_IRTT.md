---
title: "TCP Retransmissions and IRTT"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by bombarde on 2009-03-25
I am working on a research project that involves an extremely slow link.  I am trying to establish a connection to a server, which it eventually does, but with unnecessary SYN packets.  On my Ubuntu 8.10 installation, the first retransmission occurs after 3 seconds, followed by another after 6, 9, 12, 24, and 48 seconds.  The RTT of the first packet is longer than 3 seconds, but it does reach the destination and start the handshaking protocol.  The rest of the SYN packets are just wasted resources.  I have looked at iproute2 and its ability to change the rtt, rttvar, and rto_min parameters.  However, I experience two problems with this approach.  For one thing, the values being set are not the ones I supply.  For instance, the command "sudo ip route add 10.0.0.2 rtt 5secs dev tun0" sets the rtt not to 5 seconds but to 168 ms, according to "sudo ip route" with no arguments.  Moreover, the retransmission schedule is still the same as above, starting at exactly 3 seconds.  Is this the right approach to the allowing more time before a SYN retransmission?  If not, can you please point me in the right direction?  Thanks!

---

