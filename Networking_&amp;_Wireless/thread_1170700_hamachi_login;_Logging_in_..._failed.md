---
title: "hamachi login; Logging in ... failed"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by oneiric on 2009-05-26
I cannot login to hamachi.  

```
e@e-desktop:~$ hamachi login
Logging in ... failed
```

I have to report the same thing as [here]("http://ubuntuforums.org/showthread.php?t=610905"), basically

    * I am able to login to hamachi with this machine on my home network, so I know that hamachi works fine and is installed correctly.
    * Now that I'm on a new network, I can't login with this machine. HOWEVER, the really weird thing is that hamachi logs in just fine on the same machine running XP via VirtualBox, suggesting that something is weird about ubuntu


Typing 'ifconfig' returns something like:

```
ham0      Link encap:Ethernet  HWaddr d8:43:f9:4b:5f:3g  
          inet6 addr: ef80::g422:h0rr:fs8b:7e2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

```

so it appears that a ham0 interface is defined but there is no hamachi IP address.   Supposedly 'sudo tuncfg' should generate an IP address that looks like 5.x.x.x in the ham0 interface.


My firewall has the "off" configuration, which I verified by the output of '/sbin/iptables -L -nv'

```
Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination
```


Hamachi login seems to be a common problem.  Anyone else out there getting it to work?

---

### Post by Mantaraya on 2009-06-04
I have the same problem. 
Although it worked a couple of times before I ran into this problem.
Is there anywere where I can find a log about what actualy is happening?

---

### Post by danielsender on 2011-12-14
I have exactly the same problem on 11.10. On the other hand, the same beta runs fine on CentOS and the windows version also runs well. Did you ever solve the issue?

Thanks.

---

### Post by dienert on 2012-02-08
I still get this issue. Did anyone solve that?

---

### Post by olof_ on 2012-02-09
same issue here. Would appreciate any help please.

---

### Post by huyie on 2012-02-13
same issue here. logmein-hamachi_2.1.0.17-1_amd64.deb seems to install fine. couldn't find any reference to tuncfg which seems to be only needed in the the older version 0.9.9.9. Installed tunctl via uml-utilities but still doesn't work.

---

