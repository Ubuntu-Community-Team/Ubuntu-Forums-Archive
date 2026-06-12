---
title: "Multiple DNS Servers"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by Dooley on 2010-09-16
I'm trying to use 2 DNS servers on ubuntu for 2 wildcard urls.

example_a.dev and example_b.dev

example_a.dev is my local machine(with bind9) and example_b.dev is a remote dns machine(running ubuntu with bind9).

I've configured my resolve.conf like this.

search example_a.dev
nameserver 192.168.1.1
search example_b.dev
nameserver 192.168.1.2

But example_b.dev is never resolving.

I also tried using a forwarder in /etc/bind/named.conf.options

  forwarders {
    192.168.1.2;
  };  

But again example_b.dev never gets resolved. Without the example_a config settings example_b works fine.

---

### Post by e79 on 2010-09-16
Have you tried somehting like this instead :
 
search example_a.dev example_b.dev
nameserver 192.168.1.1
nameserver 192.168.1.2
 
I beleive this is the correct way to do it. Reboot the computer afterward, verify that the entries have not changed and retry your tests.
 
Tell me if it helps.

---

### Post by Dooley on 2010-09-17
It's a bit flaky but that appears to have solved it.

Many thanks!

:)

---

### Post by e79 on 2010-09-17
My Pleasure  :p

---

