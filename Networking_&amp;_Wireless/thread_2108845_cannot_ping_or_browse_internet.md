---
title: "cannot ping or browse internet"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by narenvenkat on 2013-01-25
Hi all ):P

i cannot browse internet or ping my gateway (iphone 5 tethered) on ubuntu 12.10 , i have checked my ip etc .. any ideas what is blocking . i guess its mostly to do with my iphone tethering as i can browse internet when i am connected to access points at work 

please advise ....


thanks in advance

naren

dell E5420 , core i5 , 8gb ddr3 ,ubuntu 12.10 x64 bit.

---

### Post by praseodym on 2013-01-26
Please show the outputs of:
```

route -n
lsmod
ifconfig -a
ping -c 4 www.ubuntuusers.de
ping -c 4 213.95.41.11
```
Check also here:

[http://askubuntu.com/questions/83484/what-is-the-current-state-of-apple-device-iphone-ipod-etc-support](http://askubuntu.com/questions/83484/what-is-the-current-state-of-apple-device-iphone-ipod-etc-support)

Obviously, its an Apple-problem.

---

