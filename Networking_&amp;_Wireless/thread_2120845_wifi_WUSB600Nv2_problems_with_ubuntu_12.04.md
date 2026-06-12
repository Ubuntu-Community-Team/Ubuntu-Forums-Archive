---
title: "wifi WUSB600Nv2 problems with ubuntu 12.04"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by simsim10912 on 2013-02-27
Hi Everybody,
First, please excuse me for my bad English... I'll try my best! 

I've just install the 12.04 version of ubuntu on my desk computer.
But the wireless is not detected at all...

I founded some articles about it on french sites, but I'm blocked at some steps of the process...

Ask me what you need to help me, and I'll tell you ASAP...

Thanks a lot

---

### Post by simsim10912 on 2013-02-28
Has anybody an idea for me? How can I help you with codes?

---

### Post by sully101 on 2013-03-03
The output of the following commands would be helpfull.

Boot without the adapter plugged in and then do a ```
tail -f | dmesg
```
Plug the adapter in and see what happens in the terminal ( ctrl+c ) to exit the terminal when you've copied the output

The results of the following with the adapter plugged in might also be helpfull

```
lsusb
```
```
lsmod
```

There seems to be a discussion on it here [http://community.linksys.com/t5/Wireless-Adapters/UBUNTU-WUSB600N-v2-WORKS/td-p/318026]("http://community.linksys.com/t5/Wireless-Adapters/UBUNTU-WUSB600N-v2-WORKS/td-p/318026"), the last post may be of interest ?

---

