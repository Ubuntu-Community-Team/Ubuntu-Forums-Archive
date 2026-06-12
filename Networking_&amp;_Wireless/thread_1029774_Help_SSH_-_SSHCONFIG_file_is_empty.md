---
title: "Help SSH - SSHCONFIG file is empty?"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by jp.d on 2009-01-03
Hi,

I am new to Ubuntu and I am trying to use SSH. I have installed Client & server. But when I look at the SSHDCONFIG file, it is empty. Could any once please help me out configuring the SSH.

Thanks, 
JP

---

### Post by Iowan on 2009-01-04
/etc/ssh/sshd_config is empty? Sounds kinda odd... I've attached the one from my Hardy LAMP server (rename it without the .txt).

---

### Post by albinootje on 2009-01-04
> **jp.d said:**
>  I am new to Ubuntu and I am trying to use SSH. I have installed Client & server. But when I look at the SSHDCONFIG file, it is empty. Could any once please help me out configuring the SSH.


After :
```

apt-get install ssh

```
You should have a non-empty /etc/ssh/sshd_config after that.

---

