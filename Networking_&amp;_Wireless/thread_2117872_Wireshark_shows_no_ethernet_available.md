---
title: "Wireshark shows no ethernet available"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by ivanhoe77 on 2013-02-19
Wireshark does not show any ethernet interfaces available for capture, on Ubuntu 12.1, Kubuntu 12.1 and Mint14. However, same computer and same Wireshark on SuSE 12.1 shows eth0, lo, etc.. available for capture.
 Why? :(

---

### Post by sanderj on 2013-02-19
Start with

```
sudo wireshark

```
HTH

---

### Post by haqking on 2013-02-19
> **ivanhoe77 said:**
> Wireshark does not show any ethernet interfaces available for capture, on Ubuntu 12.1, Kubuntu 12.1 and Mint14. However, same computer and same Wireshark on SuSE 12.1 shows eth0, lo, etc.. available for capture.
 Why? :(

[https://www.wireshark.org/faq.html#q9.1](https://www.wireshark.org/faq.html#q9.1)

however you shouldnt run wireshark with sudo/root or at least it is not recommended.

[http://wiki.wireshark.org/Security#Administrator.2Froot_account_not_required.21](http://wiki.wireshark.org/Security#Administrator.2Froot_account_not_required.21)

I always run it as root but I know what I am doing, you obviously dont so read the above link.

Peace

---

### Post by jonobr on 2013-02-20
You could always open a terminal and type
(using eth0 as an example)
```
tcpdump -w trace.pcap  -i eth0 -s 1600  
```
Then you could import that file into your wireshark.

You can also limit the command line if you wanted to filter by port destination, host , protocol etc....

---

