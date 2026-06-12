---
title: "rsync"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by nunojpg on 2009-11-19
I'm using rsync to transfer aprox 1,000,000 files. Both computers are in the internal 100MB network but the transfer speed doesn't go over 60KB/s. How can I diagnose the problem?

1995/240/WHIT2400.95D.Z
      305587 100%   57.18kB/s    0:00:05 (xfer#634, to-check=896559/897271)


Regards

---

### Post by Lars Noodén on 2009-11-20
> **nunojpg said:**
> I'm using rsync to transfer aprox 1,000,000 files. Both computers are in the internal 100MB network but the transfer speed doesn't go over 60KB/s. How can I diagnose the problem?

1995/240/WHIT2400.95D.Z
      305587 100%   57.18kB/s    0:00:05 (xfer#634, to-check=896559/897271)




I'm willing to bet that the internal network is 100Mb not 100MB.  

Some rules of thumb: divide by about eight (8 bits per byte, but there can be stop bits, parity bits, etc,) then estimate about 95% of that to account for overhead for the management of the connections.  

Are you using compression at all?  Please show how you are invoking rsync.

---

### Post by nunojpg on 2009-11-20
> I'm willing to bet that the internal network is 100Mb not 100MB. 

Very amusing...

> Some rules of thumb: divide by about eight (8 bits per byte, but there can be stop bits, parity bits, etc,) then estimate about 95% of that to account for overhead for the management of the connections.

I also forget to tell that it is ethernet. Not a serial link. Always good to remember stop bits.


> Are you using compression at all? Please show how you are invoking rsync. 

Problem was with a the network card driver on one of the computers. Solved.

---

