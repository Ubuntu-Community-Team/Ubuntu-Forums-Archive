---
title: "PPPoE connection problem with pppoeconf"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by abraxyz on 2011-03-12
I've set up a PPPoE connection for my ADSL modem with pppoeconf tool, and I can connect with the usual command "sudo pon dsl-provider", but everytime I restart my PC and try to connect again with the same command, connection isn't established even though the plugin is loaded:

```
$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
```So, I have to go through the pppoeconf dialog again, and it works after that, which is kind of strange.

Help is much appreciated. Thanks.

---

### Post by jimbean on 2011-03-13
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by dineshs on 2011-03-14
Please try step1 and 2 [here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2") then sudo pon dsl-provider 
Note:You may also try Network manager for connecting DSL as explained in step-3

---

### Post by abraxyz on 2011-03-17
Hey! That actually worked. Sorry for the late response. Thank you so much.

---

### Post by dineshs on 2011-03-17
Happy to hear that .Please mark the thread as solved via thread tools

---

### Post by foobantu on 2012-07-07
Hi,

I was having the exact same issue. I followed your  instructions and now its working fine.

Thank you very much :)

---

### Post by wildmanne39 on 2012-07-07
Old thread closed.

---

