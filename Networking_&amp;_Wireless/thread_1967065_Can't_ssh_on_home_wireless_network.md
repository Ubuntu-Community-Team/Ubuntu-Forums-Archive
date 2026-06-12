---
title: "Can't ssh on home wireless network"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by olwe on 2012-04-27
Oddly, I can use Nautilus, but ssh at the terminal won't get me to my other home computer. On 192.168.0.7 is a U11.10 desktop running sshd. As I said, Nautilus gets me in fine, though. 

```
ssh -v olwe@192.168.0.7:2222
```

```
sh: Could not resolve hostname 192.168.0.7:2222/home/olwe: Name or service not known
```

Another sshd problem: I set up Ubuntu 12.04 Server on another home computer. ifconfig says the wlan0 addr is 192.168.0.6 but on other machines I can't get in, although I can ping that address just fine from other boxes. It prompts me for a password, then keeps saying the password is wrong. Likewise if I try on the machine itself with ssh me@localhost. Bad password it keeps saying.

Again, server:12.04
other two boxes: 11.10

---

### Post by olwe on 2012-04-27
Okay, solved it. The proper syntax is apparently not address, colon, port but ssh -p <portnumber> . Didn't know that.

The other problem resolved itself when I adjusted the sshd_config. I had some mistakes.

---

