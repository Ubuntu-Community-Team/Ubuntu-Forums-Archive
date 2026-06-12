---
title: "What is lo?"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by BradleyAtkins on 2010-10-03
Hi

Bit of a novice about networking, can someone explain to me what the significance is of the lo setting shown below: -

```
 System information as of Sun Oct  3 12:00:36 BST 2010

  System load:  0.04               Processes:           104
  Usage of /:   0.7% of 219.30GB   Users logged in:     1
  Memory usage: 3%                 IP address for lo:   127.0.0.1
  Swap usage:   0%                 IP address for eth0: 192.168.0.2
```

I have just installed server edition on a machine and set its IP to 192.168.0.2 on my home network. I see this IP address on the login screen for "lo" as 127.0.0.1.

Can some one tell me what this is referring to and what significance it has on my network?

Cheers

---

### Post by wojox on 2010-10-03
It's short for [Loopback]("http://en.wikipedia.org/wiki/Loopback"), it's a dummy network interface that goes directly back to the computer.

---

