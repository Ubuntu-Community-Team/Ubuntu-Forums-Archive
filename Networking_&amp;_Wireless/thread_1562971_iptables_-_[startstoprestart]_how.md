---
title: "iptables - [start|stop|restart] how??????"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by NiGhtMarEs0nWax on 2010-08-28
how can i restart the iptables service??

```
/etc/ini.d/iptables start|stop|restart
```

does not work, 

```
service iptables start|stop|restart
```

does not either. i am not interested in an abstract script that i don't understand. the purpose was to learn how to use iptables across many distros, not just the unique and awkward way ubuntu does it.

all i want to do is write a shell script that i can load and run. be able to restart the service; simple. please, _just a straight answer_, no more guides, i am sick of guides, they almost never contain the information i am looking for, otherwise i wouldn't be here asking.


Thank you.


sorry, i am a bit frustrated with this, it always nips my brain when the most basic information is not available.

and if anyone wishes to explain the devil [thumbs down] icon feel free, i did not personally use or put it there. i opened a thread about it, [http://ubuntuforums.org/showthread.php?t=1555209](http://ubuntuforums.org/showthread.php?t=1555209)

---

### Post by BkkBonanza on 2010-08-28
iptables is a kernel module not a service. You cannot "stop" it.

**man iptables** for info on how to control it.

**sudo iptables -F**  will flush the current rules (which disables it)

**sudo iptables -A ...options...**  is how to add rules

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

See iptables-save and iptables-restore for saving/restoring cfgs.

I don't think Ubuntu does iptables any differently than the other distros. In my recollection of using it on Centos/RedHat it was the same.

If you want to avoid low-level iptables commands then one of the higher level iptables "managers" like ufw / gufw would be easier.

---

