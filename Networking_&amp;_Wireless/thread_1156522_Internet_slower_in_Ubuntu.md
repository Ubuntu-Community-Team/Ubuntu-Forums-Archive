---
title: "Internet slower in Ubuntu?"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by Lil Jimmy on 2009-05-11
So I've noticed that my internet connection is twice as slow in Ubuntu as in Windows XP. I took a speedtest.net test to confirm what I thought, and it's true. I've gone from 525 kB/s to 218 kB/s. Odd, no?

I'm connected directly to my router. I stopped the torrents but that's not making a difference.

---

### Post by Crafty Kisses on 2009-05-12
It's possible that you have IPv6 enabled and that's causing the Internet to run slower, first I would check if you have IPv6 running before we "try" disabling it, run the following command in Terminal and see what it brings back:
```
ip a | grep inet6
```
If you get results similar to the following:
```
inet6 ::1/128 scope host
```
Then you have IPv6 enabled. I want to see if that's the problem first.

---

### Post by Lil Jimmy on 2009-05-12
> **Codename said:**
> It's possible that you have IPv6 enabled and that's causing the Internet to run slower, first I would check if you have IPv6 running before we "try" disabling it, run the following command in Terminal and see what it brings back:
```
ip a | grep inet6
```
If you get results similar to the following:
```
inet6 ::1/128 scope host
```
Then you have IPv6 enabled. I want to see if that's the problem first.

Yup, that's the problem then.

---

### Post by Lil Jimmy on 2009-05-12
I tried what this person said:

> **mhael said:**
> There's an easy way: instead of changing **aliases** file, create fie named **bad_list** in **/etc/modprobe.d** containing this line:
```
alias net-pf-10 off
```Now reboot and voila, no IPv6 on your system!

This method will work even if /etc/modprobe.d/aliases get replaced at some update.

...But I did another speedtest.net test and I'm still slow.

---

### Post by Lil Jimmy on 2009-05-12
Bump?

---

### Post by Crafty Kisses on 2009-05-13
Once you blacklisted the IPv6 module did you make sure it was disabled by running the following command?
```
ip a | grep inet6
```

---

