---
title: "How to connect up at system boot"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by uvanov on 2013-05-23
Hello, Dear Friends!

I find it quite boring to run 

```
sudo pppoeconf
```

every time I want to connect to Internet after boot. In 

Ubuntu Documentation > ADSLPPPoE > Boot Issues

I've found:

Below is the template that will bring the connect up at system boot: 
```

auto eth0 
iface eth0 inet ppp
           pre-up /sbin/ip link set dev eth0 up
           provider dsl-provider         
           post-down /sbin/ip link set dev eth0 down
```

I've tried to type

```
sudo auto eth0
```

but nothing happened.

Could you please explain me how to enter this code in the konsole?

---

### Post by Cheesehead on 2013-05-23
That template belongs in your /etc/network/interfaces file instead of typed into the console.

---

### Post by uvanov on 2013-05-24
Thank you!

---

