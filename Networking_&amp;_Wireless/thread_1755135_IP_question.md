---
title: "IP question"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by Diametric on 2011-05-10
If my IP is 192.168.1.3 and my subnet is 255.255.255.0 how is that expressed in the format of 192.168.1.3/?

trying to wrap my mind around subnets....

thanks!

---

### Post by Toz on 2011-05-10
192.168.1.3/24

CIDR subnet mask notation is really the number of binary 1s in the subnet mask. The value 255 requires 8 bits (in the format of 11111111) to express. So, 3*8=24.

---

### Post by Diametric on 2011-05-10
Ah - very cool.  I appreciate the explanation as opposed to just the answer.  Many thanks on your quick reply.  

No need to reply - but I'm still trying to figure out how class identification is "used' even though we've implemented CIDR.  I'll get it one day...just got to keep reading.

cheers!

---

