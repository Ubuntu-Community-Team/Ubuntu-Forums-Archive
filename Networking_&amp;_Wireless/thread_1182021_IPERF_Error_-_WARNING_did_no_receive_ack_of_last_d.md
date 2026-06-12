---
title: "IPERF Error - WARNING: did no receive ack of last datagram"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by michelob22 on 2009-06-08
Hello,

I'm trying to create a test using iperf. Using UDP, I set the size of the packets with -l, and set the amount of data to send with -n. 
However, the last packet will not be acknowledge from the server so I receiver this error:

WARNING: did not receive ack of last datagram after 10 tries.

If I use the -l option independently, it works fine. The -n option needs the packet length to be an integer multiple of the amount of data needed to send. 

Also, when using the -t option instead of the -n option, I still receive the same error. 
I trace the transmissions using tcpdump, and it transmits the 10 extra packets. 

Does anyone know how to fix this?

I need to send variable length packets for different durations. Sometimes sending 1 packet only, or sending 10 packets, etc.

Thanks,
Miklos Christine

---

### Post by michelob22 on 2010-04-15
Errors is produced when downloading iperf from sourceforge and compiling it.
The fixed versions of iperf are provided in synpatic package manager.

---

