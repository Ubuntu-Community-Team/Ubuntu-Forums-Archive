---
title: "Yet Another Ethernet Problem"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by fetimo on 2010-06-19
Hullo there,

tl;dr: ethernet stopped working overnight.

Background: 
I was bored and wanted to do something with my old computer so decided to make it a place where the family could drop in files and share things. I started off by installing the server edition but was quickly out of my depth so wiped that and did a fresh install of the desktop version. I got it to the point where I could view the shared folders and write to it and was very pleased as I went to sleep watching a Gardeners' World special from my new favourite computer via my laptop. I should also note, I removed a lot of programs that wouldn't be needed (OOo, games, etc).

The problem:
Between 3am and 9am (I didn't get much sleep) the computer disconnected from the network and won't reconnect. It's a wired connection.

What I've tried:
Rebooting the computer, restarting the router, disconnecting and reconnecting the cable on both ends. I've checked the log files to see if anything was automatically installed overnight but apart from some cron stuff there's nothing weird (that I can see). I've also tried running from the LiveCD to connect but again, no luck which suggests a hardware problem (which is rather worrying).

ifconfig:
```

eth0     Link encap:Ethernet HWaddr 00:13:8f:a4:2c:50
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
         RX bytes: 0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt: 20

lo       Link encap: Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:157 errors:0 dropped:0 overruns:0 frame:0
         TX packets:157 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
         RX bytes:13838 (13.8 KB)  TX byes:13838 (13.8 KB)

```

Any advice and help is super appreciated =)

---

### Post by ajgreeny on 2010-06-19
I do not know if this is relevant or not but my ifconfig contains extra lines in comparison to yours.
```
eth0      Link encap:Ethernet  HWaddr 00:11:d8:65:f0:2d  
          [COLOR=Red]inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe65:f02d/64 Scope:Link[/COLOR]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4286682 (4.2 MB)  TX bytes:688384 (688.3 KB)
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14013 (14.0 KB)  TX bytes:14013 (14.0 KB)
```

Perhaps this is a symptom of whatever is wrong, but if not, I can't help more.

---

### Post by fetimo on 2010-06-19
Hey ajgreeny,

Thanks for your reply, I'm only guessing here but those extra lines are probably because yours is connected to the router whereas mine isn't even getting that far :(

---

### Post by fetimo on 2010-06-20
Turns out it was one of those blindingly obvious solutions that had nothing to do with Ubuntu, the ethernet cable had been broken, probably pesky birds!

---

