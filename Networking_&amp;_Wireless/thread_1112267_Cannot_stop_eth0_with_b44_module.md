---
title: "Cannot stop eth0 with b44 module"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by laptopbob on 2009-03-31
I recently switched from the generic kernel to the rt kernel, and everything works fine except I cannot shut down my computer anymore; it just hangs indefinitely. 

After searching the forums I found a similar problem where the solution involved stopping eth0 before shutting down. However, when I try to stop eth0 using:
```
ifconfig eth0 down
``` it simply hangs. In fact, I cannot even kill the ifconfig command using kill -9! Whenever I try to stop eth0, or even unload the b44 module, the command freezes in the terminal and I cannot kill the process. The output of DMESG is a long string of:

```

[  558.435390] eth0: late interrupt.
[  558.536592] eth0: late interrupt.
[  560.080669] eth0: late interrupt.
```

Searching on google I found a similar bug from 2006 in Fedora, but it appears to have been fixed and this is the only reference I can find to this kind of behavior. [https://bugzilla.redhat.com/show_bug.cgi?id=219277]("https://bugzilla.redhat.com/show_bug.cgi?id=219277")

It appears this problem is related to the b44 module. If I don't plug in my wired ethernet cable I can shut down and unload the b44 module no problem. Once I plug in the ethernet cable the b44 module cannot be unloaded and I cannot stop eth0 or shut down my computer. 

Strangely enough, I can still use access the internet through eth0, I just can't kill it.

Any help is appreciated.

---

