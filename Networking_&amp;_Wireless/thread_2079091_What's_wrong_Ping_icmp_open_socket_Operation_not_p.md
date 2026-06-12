---
title: "What's wrong? Ping: icmp open socket: Operation not permitted"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by El Potro on 2012-11-01
Hello everybody,

I've been installing and configuring 12.04. It was working fine, but after some reboots I started to see some problems with the network.

First, when the computer started up, it was displaying (something like) this message:
[B][SIZE="2"]
Waiting for networking configuration[/SIZE][/B]

And then,
[B][SIZE="2"]
waiting 60 seconds[/SIZE][/B]

Finally 

**No full network configuration**

So searching the web I found out it had to do with the configuration at /etc/network/interfaces. So I partially emptied the file (removed my eth0 configuration) and tried to create the network configuration directly with **nm-connection-editor**. 

Surfing the web works, but when I want to ping with a regular user (to any address), I get

```
Ping: icmp open socket: Operation not permitted
```

It's funny though, because if I add sudo, the ping operation executes normally.

I tried going back and re-adding the /etc/network/interfaces configuration, but it's the same.

Now I don't know what I should do, or what is the cause of the problem.

Any help will be greatly appreciated.

---

### Post by El Potro on 2012-11-01
I did look around but I didn't see it. Luckily I found the answer here:

[http://ubuntuforums.org/showthread.php?t=927709](http://ubuntuforums.org/showthread.php?t=927709)

```
sudo chmod u+s `which ping`
```

---

