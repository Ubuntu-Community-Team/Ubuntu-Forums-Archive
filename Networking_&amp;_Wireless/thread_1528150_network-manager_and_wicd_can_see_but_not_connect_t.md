---
title: "network-manager and wicd can see but not connect to network"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by fiddler616 on 2010-07-10
Hello,

I recently put Linux on a Thinkpad T40 I got. The wireless card works out of the box--I can see nearby networks. However, I can't connect to mine. network-manager would try (spin spin spin), fail, ask for the password, and then go back to the beginning and repeat indefinitely. This happened to me on a different computer, and on that one all I had to do was use wicd instead of network-manager. So I installed wicd, but it's not working either--it hangs at "Obtaining IP address".

I've found many, many threads with people who had the same problem, but none of their fixed worked for me.

I also tried to get wifi going manually, using [this]("http://ubuntuforums.org/showthread.php?t=571188")  guide, but that didn't work.

So...what do I do?

Thanks in advance.

---

### Post by fiddler616 on 2010-07-12
Solved by upgrading the kernel to 2.6.28-19 by running

```
sudo apt-get dist-upgrade
```

---

### Post by Iowan on 2010-07-12
Out of curiosity, did that take you to 9.10 - or beyond?

---

### Post by fiddler616 on 2010-07-12
> **Iowan said:**
> Out of curiosity, did that take you to 9.10 - or beyond?

I'm actually using Crunchbang, whose latest stable version is based on Jaunty (next version will be based on Debian, but is still Alpha).

I'm still using the Jaunty repositories and whatnot. My kernel is: 2.6.28-19-generic.

So you make your own decision about what version that puts me in.

---

