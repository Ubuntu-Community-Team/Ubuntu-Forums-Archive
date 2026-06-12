---
title: "Bridge issue (broke down since kernel upgrade)"
date: 2005-12-25
forum: Networking &amp; Wireless
---

### Post by shadowcode on 2005-12-25
Hello,

Since I installed Kernel 2.6.10-6-686 (or possibly before, didn't update in a while), bridging support died.

Whenever I try to initialise a bridge (brctl add), I get the following error:
```
add bridge failed: Package not installed
```

I uninstalled/reinstalled the bridgeutil package, but no dice.
I suspect that the kernel was compiled with bridging support off, how do I check and how do I fix this?

Thanks in advance for any help!

---

### Post by shadowcode on 2005-12-25
This person has the same problem:
[http://ubuntuforums.org/showthread.php?t=101132](http://ubuntuforums.org/showthread.php?t=101132)

---

### Post by Lambert on 2005-12-25
I may not be correct on this but I'll see if I can help you.

run this command 

```
cat /boot/config-`uname -r` | grep -A 5 CONFIG_BRIDGE
``` 

your line should look like this.

CONFIG_BRIDGE=m

this means that bridging is configured in the kernel as a module. I believe if it has an =y it is configured into the base of the kernel. Either one of these means that bridging is enabled in the kernel.

For help setting up look at the documentation in /usr/share/doc/bridge-utils

The homepage of the bridge-utils project is found here. You may find help there.

[http://linux-net.osdl.org/index.php/Bridge]("http://linux-net.osdl.org/index.php/Bridge")

---

### Post by shadowcode on 2005-12-25
Thanks for your reply. CONFIG_BRIDGE is indeed set to m.

Dug around a bit more in the logs, and there's a related error message.
```
localhost kernel: bridge: Unknown symbol br_fdb_update
```

---

