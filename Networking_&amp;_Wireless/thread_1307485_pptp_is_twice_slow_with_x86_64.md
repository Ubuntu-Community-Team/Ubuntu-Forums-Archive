---
title: "pptp is twice slow with x86_64"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by uvi on 2009-10-31
I compared pptp performance between i386 and amd64 versions of ubuntu 9.10. My cpu e8400. Config files was the same, network manager completely removed. I found on amd64 pptp as twice slower as on i386 (avg 5,39M/s on i386 and 2,78M/s on amd64). Near windows pptp server (connected in one giga stacked switch) on ubuntu 9.10 i386 without pppoe i have 8,93M/s over 1gbit link on Intel(R) Pentium(R) 4 CPU 3.00GHz.
My pptp connection established over pppoe, but in both cases pppoe transfer data with maximal speed (100mbit, tested with wget -O /dev/null).

**/etc/ppp/peers/test:**
```

remotename test
persist
linkname test
ipparam test
pty "pptp <my_ip> --nolaunchpppd "
name test
require-mppe
nomppe-40
refuse-eap
noauth
file /etc/ppp/options.pptp
noproxyarp
maxfail 0

```**/etc/ppp/options.pptp**:
```

lock
noauth
nobsdcomp
nodeflate

```

---

### Post by Joe_Bishop on 2009-11-18
I have the same issue with xl2tpd. Filled a bug.
[https://bugs.launchpad.net/ubuntu/+source/pptp-linux/+bug/484794](https://bugs.launchpad.net/ubuntu/+source/pptp-linux/+bug/484794)

---

### Post by Joe_Bishop on 2009-11-18
I have the same issue with xl2tpd. Filled a bug.
[https://bugs.launchpad.net/ubuntu/+source/pptp-linux/+bug/484794](https://bugs.launchpad.net/ubuntu/+source/pptp-linux/+bug/484794)

---

### Post by BbICEP on 2009-11-19
I have the same issue (both pptp and xl2tpd suffer from it). Please, confirm this bug: [https://bugs.launchpad.net/ubuntu/+source/pptp-linux/+bug/484794](https://bugs.launchpad.net/ubuntu/+source/pptp-linux/+bug/484794)

---

### Post by uvi on 2010-10-13
I found a solution - use accel-pptp.
With ubuntu 10.10 x64 I have now ~95Mbit pptp with mppe 128 over pppoe over 100mbit link.

---

