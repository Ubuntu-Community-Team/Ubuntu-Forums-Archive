---
title: "Speed-up your internet connection to 200%!!!"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by armandecastro on 2011-10-29
UBUNTU 11.04

WORKING!! put this in /etc/sysctl.conf

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

then run as root # sysctl -p

<snip>

---

### Post by armandecastro on 2011-10-29
put the code at the bottom of /etc/sysctl.conf then run in root sysctl-p

---

### Post by cbowman57 on 2011-10-29
What did you come up with?

---

### Post by Dangertux on 2011-10-29
Not sure I would recommend doing this. Editing /etc/sysctl.conf can be tricky.

While that isn't the worst thing in the world you could do to it the minor performance gain, may not be notable over the potentially higher resource usage for some users. You should probably include some type of warning that you're deviating from default kernel tuning.

Matter of fact, I'm not sure that's even supported here.

---

### Post by armandecastro on 2011-10-29
backup your /proc/sys/net and /proc/sys/ipv4 in case you do not want the effect.

I am enjoying my ubuntu internet connection it is really fast.

Thank you.

---

### Post by jonobr on 2011-11-03
Given the subject line, I was expecting pitches for ED pills and performance enhancers in this thread.:lolflag:

---

### Post by cbowman57 on 2011-11-03
> **venmalathy said:**
> To increase the speed of the Internet  surely You can use the steps above,Because it worked for my speed increasing process!! It's good to   increase my speed of the Internet....Before using  this tips My internet speed is slow,now my speed is Good ..My uploading  speed 123Kbps,Downloading speed 1956Kbps I checked my speed at here [Ip-details.com]("http://www.ip-details.com/internet-speed-test/")

I was just curious as to the source, or sources, that helped you arrive at it.

I've been seeing "Speed your internet xxx%" for years, if it were possible I don't think it would be a secret.  However, I'm not going to dismiss what you posted, just want to know how you arrived your improvement.

---

### Post by chili555 on 2011-11-03
I am a bit skeptical that the exact same settings will be equally effective on DSL, cable, fiber, etc. and no matter what your ISPs speed is. Please see: [http://www.dslreports.com/tweaks](http://www.dslreports.com/tweaks)

[http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346)

---

