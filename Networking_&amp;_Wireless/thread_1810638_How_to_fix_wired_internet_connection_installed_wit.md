---
title: "How to fix wired internet connection installed with ubuntu ? help?"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by Missconfiguration on 2011-07-23
I have an ibm think pad and for some reason the internet(firefox) stop working and i don't know why , the netwprl settings have disappeared or anything on fixing it , yes i have tried restarting the modem but that hasn't work ethier Also i don't really know where the re-start disk so is there anyway i can fix it with out the disk?help please?

---

### Post by 2F4U on 2011-07-23
Can you show the output of the command

```
ifconfig -a
```

in a Terminal?

---

### Post by Missconfiguration on 2011-07-23
You want me to put that in the terminal of the laptop? i did and it said ifcanfig-a: command not found 
[EMAIL="tabby@tabby-laptop:~/desktop$"]tabby@tabby-laptop:~/desktop$[/EMAIL]

---

### Post by bkratz on 2011-07-23
> **Missconfiguration said:**
> You want me to put that in the terminal of the laptop? i did and it said [COLOR="Red"]ifcanfig-a[/COLOR]: command not found 
[EMAIL="tabby@tabby-laptop:~/desktop$"]tabby@tabby-laptop:~/desktop$[/EMAIL]




Spaces and spelling are important.

---

### Post by Missconfiguration on 2011-07-23
Well i re-did it and it gave me alot so i' guessing you want the hole thing? 
 
eth0      link encap:ethernet  HWaddr 00:09:6b:53:00:31
            BROADCAST MULTICAST MTU:1500 Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 frame:0
            collisions:0 txquelen:1000
            RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
 
irda0    Link encap:IrLAP  HWaddr 00:00:00:00
           NOARP MTU:2048 Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0    txqueuelen:8 
           RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
 
Lo        Link encap: Local Loopback 
           inet addr:127 .0.0.1 Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING MTU:16436 Metric:1
           RX packets:12 errors:0 dropped:0 overrunes:0 frame:0 
           TX packets:12 errors:0 dropped:0 overrunes:0 carrier:0 
           collisions:0 txqueuelen:0 
           RX bytes:720  (720.0 B)   TX bytes:720  (720.0 B)

---

