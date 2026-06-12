---
title: "How to change somaxconn in Ubuntu 10.10"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by highlander2 on 2010-12-11
I need to run stress-tests on my Ubuntu 10.10 Desktop 64 bit, the test opens 200 simultaneous connections to a socket. 

cat /proc/sys/net/core/somaxconn
128

I need to change somaxconn to 512

 I edited /etc//etc/sysctl.d/10-network-security.conf
added line
net.core.somaxconn=512

Then re-booted 
cat /proc/sys/net/core/somaxconn
128

As you can see, the system didn't pick up somaxconn from config file.

Then I changed somaxconn manually

sudo sysctl -w net.core.somaxconn=512
net.core.somaxconn = 512

But I don't want to change somaxconn manually every time, need to configure it once per system.  I am not sure if /etc//etc/sysctl.d/10-network-security.conf is the right place for somaxconn, but editing the file works for me on another Linux box with Ubuntu 10.04 Desktop 64 bit. In 10.10 it doesn't work anymore.


I will be grateful if you help me to solve this problem.

---

