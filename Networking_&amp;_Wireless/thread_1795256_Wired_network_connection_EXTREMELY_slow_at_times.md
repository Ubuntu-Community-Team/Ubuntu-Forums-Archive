---
title: "Wired network connection EXTREMELY slow at times"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by ntnkj on 2011-07-02
I use Ubuntu 11.04 (installed on a USB stick, since the installer can't recognize partitions : [http://ubuntuforums.org/showthread.php?t=1793978](http://ubuntuforums.org/showthread.php?t=1793978) ) and Windows 7 (installed normally on my HDD)

The wired connection works fine under Win7, and sometimes also under Ubuntu, but at times it just slows down inexplicably, and it takes a few minute to open my e-mail account, for example.
I tried some of the suggestions made to other people with a similar problem, so I am using OpenDNS, and I tried different txqueuelen settings, but still it's slow...

---

### Post by ntnkj on 2011-07-03
I set up my MTU perfectly, with the help of this great thread:
[http://ubuntuforums.org/showthread.php?t=1376506](http://ubuntuforums.org/showthread.php?t=1376506)

I set MTU to 1472 now, and so far so good!

---

### Post by ntnkj on 2011-07-05
Still having problems. Here's an example:

```
ntnkj@ntnkj-HP-ProBook-4310s:~$ ping -c3 10.248.27.2PING 10.248.27.2 (10.248.27.2) 56(84) bytes of data.

--- 10.248.27.2 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

ntnkj@ntnkj-HP-ProBook-4310s:~$ 
```

I have huge packet losses on every ping test.

---

