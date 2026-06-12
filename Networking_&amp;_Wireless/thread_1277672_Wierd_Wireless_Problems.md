---
title: "Wierd Wireless Problems"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by coldfusion1313 on 2009-09-28
I have had Ubuntu 9.04 installed on my HP Pavilion dv6000 laptop for about 2 months now and the other day I could not connect to the internet but I was connect to my home network. I restarted and it still was not working. I could not go on the internet but I can still do network file transfers on wireless. So I booted of the live cd and I could connect to the internet wireless on the live cd. Is there something wrong with my ubuntu install? Please Help.

---

### Post by cariboo on 2009-09-29
It sounds like you have a dns problem, can you ping by number but not by name? Open a terminal and type:

```
ping www.google.com
```

if that doesn't work try:

```
ping 74.125.155.103
```

Please let us know what the results are.

---

### Post by coldfusion1313 on 2009-10-02
It has gotten worse the only way i can get on the Internet is by using ethernet. Ubuntu does not even see that I have a wi-fi card.

---

