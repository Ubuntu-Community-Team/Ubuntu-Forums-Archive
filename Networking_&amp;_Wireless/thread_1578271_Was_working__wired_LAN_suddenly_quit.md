---
title: "Was working : wired LAN suddenly quit?"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by jorx on 2010-09-20
* SOLVED * > An accidental Hibernate must have stopped the lan. < *SOLVED*


Hi fellow ubuntu users! I'm using Linux Mint 9 KDE edition at the moment.
I've just freshly installed it, things were going fine and I was updating software on it, downloading away, etc. It's worked fine for several boots now, a few weekends. 

Then- yesterday, after one boot it no longer has LAN connectivity! No internet!
I'm at loss how to troubleshoot it- I'm a relative NOOB so I'd appreciate any advice you can give.

Here are the results of the 'ifconfig' command, which is pretty much the only network -related command I know :-P

```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61300 (61.3 KB)  TX bytes:61300 (61.3 KB)
```

---

### Post by Iowan on 2010-09-20
Right-click Network Manager icon and verify Networking is still enabled.
[Another]("http://ubuntuforums.org/showthread.php?t=1505217") thread to check.

---

### Post by jorx on 2010-09-20
a*HA!!!
Just from reading that thread-- I recalled I accidently hibernated, and didn't boot properly. So that's the likely cause then.

However the cause to that was just as random- one time I decided to shut down the machine and the "Shutdown" button was completely missing, leaving me with log-off, restart, or hibernate. Odd :confused:

---

### Post by CharlesA on 2010-09-20
Should be able to shutdown from Alt+F2 regardless:

```
halt
```

Not sure if it'll need gksu or kdesu or whatever it's called in KDE.

---

