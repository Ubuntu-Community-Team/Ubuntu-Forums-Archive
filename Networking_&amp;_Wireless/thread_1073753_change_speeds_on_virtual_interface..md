---
title: "change speeds on virtual interface."
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by rgb96 on 2009-02-18
Hey all,

I am running Ubuntu 8.10, and I just set up a virtual machine to run Windows XP for me with VirtualBox. That all went well, and I set up a virtual bridge and a virtual interface (tap0) so I could give my virtual machine an static IP address, because I'm setting up an ssh server on the virtual machine. So I found a tutorial online and followed it and it seems to work pretty well. I can get on the internet in windows and I can ping everything in my network, except the host Ubuntu machine. I can ping from the host to the guest, but not vice versa, and my ssh is refused at port 22, although the guest has no firewalls running on it. 

I noticed that eth0 is running at 100mb/s and tap0 is running at 10 mb/s, so I tried to change the speed on tap0 with ethtool, but I get this response:

```
x@y:~$ sudo ethtool -s tap0 speed 100
Cannot set new settings: Operation not supported
  not setting speed

```

I also noticed in ifconfig that tap0 is dropping packets.

My line of thought leads me to believe that if I could change the speed, my problem would be fixed. I could be wrong though. Any ideas or thoughts pointing me in the right direction would be much appreciated.

---

### Post by rgb96 on 2009-02-18
Never mind that. I've learned now that speed on the virtual card doesn't matter one bit. However, I still can't ping from the virtual machine to the physical machine, which is still a problem.

---

