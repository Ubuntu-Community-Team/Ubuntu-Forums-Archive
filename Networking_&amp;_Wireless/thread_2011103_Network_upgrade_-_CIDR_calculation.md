---
title: "Network upgrade - CIDR calculation"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by piriton on 2012-06-26
I am going to receive a /23 network, however it's not completely clear to me, how many extra IP addresses this will provide to use.

I know you have to take away the brodcast address and you don't use .255, so does that leave 508 usable addresses ?

Networking is definitely not my strong point.

Is there a good tool to provide me with this information with these calculations.

---

### Post by hawkmage on 2012-06-26
Take a look at this link: [http://www.subnet-calculator.com/cidr.php](http://www.subnet-calculator.com/cidr.php)

---

### Post by haqking on 2012-06-26
(2^9)-2 = 510 hosts (512 before subtracting n where n is network and broadcast)

255.255.254.0 mask.

however all you said was a /23 so cant assume much more.

Peace

---

### Post by piriton on 2012-06-27
How do you determine that there are 256 IP's in a /24 ?

As I understand, a /24 is from .1 to 255.

---

### Post by The Cog on 2012-06-27
There are 256 addresses in a /24, from 0 to 255. However, the all-zeros address and the all-ones address (0 and 255) are not usable for normal hosts (255 is the broadcast address), so 1-254 are usable.

For a /23 the possible host-part addresses are 0-511 with 0 and 511 being unusable.
e.g. for network 10.10.10.0/23 the usable addresses would be 10.10.10.1-10.10.11.254.

---

### Post by haqking on 2012-06-27
> **piriton said:**
> How do you determine that there are 256 IP's in a /24 ?

As I understand, a /24 is from .1 to 255.

because all IP addresses in IPv4 are 32 bit (computers only see binary)

Binary is base 2.

2^8 (where 8 is the remainder from 32 after the 24 is subtracted) is equal to =

256

2 addresses cannot be used as addressed above.

But who cares, its all incomprehensible IPv6 now anyways...LOL ;-)

Peace

---

### Post by piriton on 2012-06-27
I think i've got it, so as an example, if I were given a /25 then there are 128 - broadcast - network address = 126 addresses, right ??

---

### Post by haqking on 2012-06-27
> **piriton said:**
> I think i've got it, so as an example, if I were given a /25 then there are 128 - broadcast - network address = 126 addresses, right ??

yep

---

