---
title: "Route and numerical addresses."
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by kleenex on 2012-08-12
Hi, I use a common cable connection, router and DHCP to obtain IP address. I disable [COLOR=Green]dnsmasq[/COLOR] service by editing [COLOR=Green]/etc/NetworkManager/NetworkManager.conf[/COLOR] file, because it was on **LISTEN** state. But it is not important. My question is related to the **route** command and some results. 

```
[COLOR=Blue]# route -Cn[/COLOR]
Kernel IP routing cache
Source          Destination     Gateway     Flags   Metric   Ref    Use Iface
192.168.1.21    192.168.1.21    192.168.1.1          0      0       0 eth0
72.233.69.4     192.168.1.21    192.168.1.21    l    0      0      19   lo
91.189.94.12    192.168.1.21    192.168.1.21         0      0       0 eth0
...
``` And many, many more. It is normal, that on some positions the Source address is something, which I do not know? For example 91.189.94.12 address. Why it is Source? 192.168.1.21 as you can guess is my address assigned by router (which is 192.168.1.1). Is this normal? And why in some cases 192.168.1.21 address (my computer) is marked as a Gateway? 

Could someone explain it to me? Thank You.

---

### Post by papibe on 2012-08-12
Hi kleenex.

That looks normal. The -C option shows the kernel's routing cache, so what you are seeing is a recent history of how network packages has been handled.

Here's an example:
```

91.189.94.12    ubuntuforms.org
192.168.1.101   my machine
192.168.1.254   my router
```
Then
```
$ route -Cn | grep 91.189.94.12
91.189.94.12    192.168.1.101   192.168.1.101   l     0      0      420 lo
192.168.1.101   91.189.94.12    192.168.1.254         0      4       39 eth0
192.168.1.101   91.189.94.12    192.168.1.254         0      0       19 eth0

```
The last 2 lines describe how do I get to the forums: via the router and using the ethernet card.
The first one is the other way around: when I receive a package from the forums which its destine is my IP, it is routed to myself using the loopback interface (lo).

In general, while diagnosing network problems, that's too much information. Usually the route table (not cache) is what is used to troubleshooting network problems ('route -n').

Does that help?
Regards.

---

### Post by kleenex on 2012-08-13
Hi **[COLOR=Navy]papibe[/COLOR]**! So everything is normal? You asked: *Does that help*? **[COLOR=Navy]papibe[/COLOR]**[COLOR=Navy][COLOR=Black], do not be silly! :-) [/COLOR][/COLOR]Your answer is simply GREAT. Explain a lot to me, really. Now I know why these "strange" addresses are identified as the source etc.

Thank You very much, **[COLOR=Navy]papibe[/COLOR]**[COLOR=Black]![/COLOR]

---

