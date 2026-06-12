---
title: "Chromium and torsocks"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by kadinski on 2011-09-02
I'm trying to socksify Chromium with torsocks so that all connections are made through tor. Unfortunately it doesn't work.   ```
torsocks chromium
```  Last message in terminal is:  ```
[1:1:18399861630:FATAL:zygote_main_linux.cc(126)] Check failed: r. Sending zygote magic failed
```  Syslog says:  ```
 Sep  2 21:00:19 kernel: [18477.344405] chromium-browse[8654] general protection ip:b383c2bd sp:bf81fdc8 error:0 in libc-2.13.so[b380e000+15a000]
``` Unfortunately this messages don't mean much to me.   What is going wrong and how can i get Chromium to work together with torsocks?

---

### Post by kadinski on 2011-09-03
Noone?

---

### Post by 666f6f on 2012-07-18
torsocks makes use of the [LD_PRELOAD]("http://linux.die.net/man/8/ld.so") environment variable, a whitespace-separated list of additional, user-specified, ELF shared libraries to be loaded before all others. It appears that [LD_PRELOAD wont work due to chromium's sandboxing]("https://bbs.archlinux.org/viewtopic.php?pid=672176#p672176").

You can still use chromium's command line switches to make it use tor, or any other proxy server. [DNS resolve requests may leak]("https://trac.torproject.org/projects/tor/wiki/doc/Preventing_Tor_DNS_Leaks"), but I can't say for sure since I haven't tested it. I put the following code in a script file called torium in ~/bin.

```

#!/bin/sh
chromium --proxy-server="socks://localhost:9050"

```

---

