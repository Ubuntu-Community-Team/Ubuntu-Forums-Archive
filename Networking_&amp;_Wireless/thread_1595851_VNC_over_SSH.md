---
title: "VNC over SSH"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by Neezer on 2010-10-13
Hi,

I'm trying to follow this guide:
[http://bodhizazen.net/Tutorials/VPN-Over-SSH/](http://bodhizazen.net/Tutorials/VPN-Over-SSH/)

i'm having problems getting my VPN over SSH to work. I am pretty sure that I've done all the right steps, but I keep getting errors when I try to log on to my server.....

Here is what I get for errors.
```

nathan@nathan-lappy:~$ sudo ifup tun0
Warning: Identity file /root/.ssh/rsa_id not accessible: No such file or directory.

channel 0: open failed: administratively prohibited: open failed
SIOCSIFADDR: No such device
tun0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFDSTADDR: No such device
tun0: ERROR while getting interface flags: No such device
tun0: ERROR while getting interface flags: No such device
Failed to bring up tun0.

```

Any suggestions would be greatly appreciated.

Thanks

---

### Post by Neezer on 2010-10-14
Bump? anyone?

---

### Post by Neezer on 2010-10-16
one final bump before I give up on this idea for now....anybody?

---

### Post by irfaancoonjah on 2013-05-02
Hello,
I am following the [http://bodhizazen.net/Tutorials/VPN-Over-SSH](http://bodhizazen.net/Tutorials/VPN-Over-SSH)

I am having the same error message.

root@theo62:~# sudo ifup tun0
SIOCSIFADDR: No such device
tun0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFDSTADDR: No such device
tun0: ERROR while getting interface flags: No such device
Failed to bring up tun0.
root@theo62:~# 

Have you been able to sort it out?
any help?

---

