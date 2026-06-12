---
title: "command to enable packet loss"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by bidur on 2013-02-25
I am searching a good way to enable packet loss. I came across this command for ubuntu. This command is supposed to make the interface wlan11 to lose 10% (0.10) of the packets it receives.

```
sudo iptables -A INPUT -i wlan11 -m statistic --mode random --probability 0.10 -j DROP

```

Is this command good to use or are there any better/easy command/methods that I can use.

Thank You.

---

### Post by Doug S on 2013-02-26
Well, that is exactly what I would do. I do not know of a better or easier way, which doesn't mean there isn't one. Here is a before and after example of using that iptables rules on one of my computers:```
doug@s15:~/sguide-1304$ [COLOR=red]sudo ping -i 0.1 -c 1000 -q test-smy[/COLOR]
PING test-smy.smythies.com (192.168.111.140) 56(84) bytes of data.
--- test-smy.smythies.com ping statistics ---
1000 packets transmitted, 1000 received, [COLOR=red]0% packet loss[/COLOR], time 99899ms
rtt min/avg/max/mdev = 0.215/0.248/0.471/0.030 ms
doug@s15:~/sguide-1304$    [COLOR=red]<<<< iptable rule added on test-smy computer.[/COLOR]
doug@s15:~/sguide-1304$ [COLOR=red]sudo ping -i 0.1 -c 1000 -q test-smy[/COLOR]
PING test-smy.smythies.com (192.168.111.140) 56(84) bytes of data.
--- test-smy.smythies.com ping statistics ---
1000 packets transmitted, 913 received, [COLOR=red]8% packet loss[/COLOR], time 100540ms
rtt min/avg/max/mdev = 0.221/0.254/0.479/0.023 ms
```

---

