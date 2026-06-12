---
title: "configure gkrellm for ssh tunnel with dynamic ip"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by kaefert66014235 on 2010-01-05
Hello!

I am using gkrellm via ssh tunnel to monitor my machine at home.

In the gkrellmd.conf on the home-machine i have this line:
```
port 19150
```

I connect to my home-machine with this command:
```
ssh -L 19151:kaefert.gotdns.org:19150 <IP> -C
```

Then I start gkrellm like this:
```
gkrellm -s 127.0.0.1 -P 19151
```

However, for security reasons, i don't want to configure my gkrellmd like this
```
allow-host     ALL
```

I have the following allow-host lines on the home-pc:
```
allow-host      localhost
allow-host      127.0.0.1
allow-host      ::ffff:127.0.0.1
allow-host      192.168.178.20
```

This works perfectly when I'm connecting from the local network, but for being able to run gkrellm via the ssh-tunnel when coming from the internet, i have to add the public ip adress that has last been given to my home-machine from my ISP, the problem is the constant reconfiguration necessary.

I have configured a dyndns.org account for that machine (with which I'm able to reach the machine), however, allow-host that dns-name doesn't work.

Has anybody an idea how to avoid the constant reconfiguration? Thank you for reading and I hope somebody can help me.

---

