---
title: "KVM public ips"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by Basti1508 on 2013-07-08
Hello together,

i've now seen a lot of posts concerning this topic, but none of them worked for me :(

I have a public server with ip 111.111.111.111 running.

I have 2 vms on it. and now i want to make these 2 vms public with the addresses:

111.222.111.112
111.232.111.113

What are the correct configs in /etc/network/interfaces for this?

Please help someone -.-

---

### Post by DJ_Max on 2013-07-08
You configure it the same way as you would a physical host. So look at the instructions for whatever distribution you're using.

---

### Post by Basti1508 on 2013-07-08
But i have to work with bridges with kvm?

how to configure this?

---

### Post by DJ_Max on 2013-07-08
Start here
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)
[http://www.linux-kvm.org/page/Networking](http://www.linux-kvm.org/page/Networking)

---

