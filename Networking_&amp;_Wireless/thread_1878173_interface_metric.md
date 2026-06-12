---
title: "interface metric"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by henge on 2011-11-09
How do you set metric on a interface so it prefferes eth0 instead on eth1

---

### Post by jonobr on 2011-11-09
sudo ifconfig eth0  metric X ?


Havent tried it but its in the manpages

---

### Post by henge on 2011-11-09
Thanks for you answer

already tried that

SIOCSIFMETRIC: Operation not supported

please help

---

### Post by jonobr on 2011-11-09
Tried it myself, get the same

note [Here]("http://ubuntuforums.org/showthread.php?t=1224046") the recommend the use of ifmetric and setting it there.

I checked and ifmetric is in the repos,

---

### Post by henge on 2011-11-09
thanks again

also tried that solution but ifmetric dosen't work on amd64

sudo ifmetric eth0 3
NETLINK: Packet too small or truncated! 92!=16!=244

found this

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=514197](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=514197)

any other suggestion ;-)

---

### Post by jonobr on 2011-11-09
Good spot, 

but this bug is 2.5 years old, Im sure the fix would have made it in by now? May be worth email the  reporter in the bug

---

### Post by henge on 2011-11-09
Thanks again

I now installed 10.4 and ifmetric is working now
so this problem is in 11.10

but I still have my problems

2 interfaces

eth0 192.168.1.x
eth1 10.44.51.x

I need to use eth1 for IPTV
so in vlc I do udp://@233.139.5.168:5501

This is working if I disable eth0
enable eth0 - bummer

So I setup eth1 without gateway and dns
make a route 2330.0.0. mask 255.0.0.0 gw 10.44.48.1

but that dosen't help much

so then I did ifmetric eth0 100 and ifmetric eth1 0

some issue disable eth0 and it works

can you help me here ,-)

---

### Post by jonobr on 2011-11-09
are you trying to route between the two networks?

is ip forwarding enabled ?

cat /proc/sys/net/ipv4/ip_forward

---

### Post by henge on 2011-11-10
Thanks for your reply

Yes I want traffic for 233.0.0.0 and 239.0.0.0 out on eth1 10.44.51.x
and all other traffic out on eth0 192.168.1.x

I will check ip forward

---

### Post by henge on 2011-11-10
aah im stupid;-)

forgot to enable ip forward

Thanks alot

---

### Post by jonobr on 2011-11-10
Great


Recommend you marked as solved for people searching on metric changing

---

