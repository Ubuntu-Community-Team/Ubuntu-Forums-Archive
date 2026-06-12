---
title: "Internet wired connection very slow"
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by Rascal74 on 2012-07-27
Hi,

Since 2 days, my internet wired connection loads web sites very slowly on Linux Mint 11, whatever browser I use. Under Windows 7 it works very well, so it's not a problem with my ISP. I tried to desactivate IPV6 without success.
There has been a lot of updates those last days, so I think it could be a problem with one of thoses updates, but I'm not sure.
Please help me to solve this problem.

---

### Post by albandy on 2012-07-27
It could be a kernel driver problem, boot with a previous kernel version and test the connection.

---

### Post by Rascal74 on 2012-07-27
Thanks for help.

I tried to boot with an older kernel but it did not solve the problem.
2.6.38.8-generic instead of 2.6.38.11-generic

---

### Post by Rascal74 on 2012-07-28
I solved the problem by myself. It was a problem with DNS.
I just manualy entered my ISP's DNS in the network manager and now it works really fine.
If it can help somebody else, just don't use automatic DNS if you have the same problem.

---

