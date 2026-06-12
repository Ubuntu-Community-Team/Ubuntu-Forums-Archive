---
title: "Find computer linked to eth0"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by Pyro.699 on 2011-04-28
Hey,

So theres a story behind this and i don't really wanna explain it xD Needless to say, i have a laptop at work, the user got logged out and now im unable to access it directly.

I have a work computer that is directly connected (through eth0) to my laptop, and that is still on:
**_ifconfig_** - on work computer
```

eth0      Link encap:Ethernet  HWaddr 00:30:1b:47:23:55
          inet addr:169.254.4.113  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: ----::230:----:fe47:----/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:4598 (4.5 KB)
          Interrupt:17

```I want to run the command "sudo shutdown -r 0" on my laptop so that it will reboot... and then auto-login to the laptop again.

If i go to ping computer i get this:
```

<name>@<work desktop>:~$ ping <laptop comp>
PING <laptop comp>.gateway.2wire.net (192.168.2.11) 56(84) bytes of data.
From <work desktop> (192.168.2.16) icmp_seq=1 Destination Host Unreachable
From <work desktop> (192.168.2.16) icmp_seq=2 Destination Host Unreachable

```That address is the one when it is connected through the wireless; but when it got logged out i guess it shuts the wlan interface off.

In short, i need to find the address of the computer on the other end of the eth0

Thanks
~Cody

---

### Post by spiky001 on 2011-04-28
Cant you just put ifconfig in the laptop if not try nmap

---

### Post by Pyro.699 on 2011-04-28
Im not at work, and the building is empty xD Otherwise id just restart it by hand >.>

---

### Post by spiky001 on 2011-04-28
how about nmap it,s in the resportories

---

### Post by Pyro.699 on 2011-04-28
I just ran it on my work computer "**nmap -v -sP 169.254.0.0/16**"

... 5 minutes later ...

The output goes by too quickly and i cant read it... ill have to run it again and put the output into a file xD

Thanks
~Cody

---

