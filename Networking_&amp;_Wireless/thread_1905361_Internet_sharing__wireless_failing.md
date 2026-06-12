---
title: "Internet sharing / wireless failing"
date: 2012-01-06
forum: Networking &amp; Wireless
---

### Post by gameguy on 2012-01-06
The wireless on my laptop is not working, because it is one of those broadcom ones, and if I'm not mistaken, they havent updated their drivers for the new kernel (I run 11.10). It is a broadcom 43224 wireless ABGN adapter. I already tried the methods in the sticky for broadcom wireless adapters, but I believe they only work for pre gnome3 releases. Or something like that, anyway.

So basically, I was left with using a really bad USB wireless adapter which drops out all the time from 1 room away. I think the easiest thing to do would be to share the wireless connection from a windows 7 laptop to my ubuntu one. I have gone (under windows) into network and sharing center > change adapter settings > wireless > properties > properties > sharing tab > tick both > settings > tick all > ok > ok.
Is there any setup I need to do from linux? The linux laptop detects that it is connected to a network, but it has no internet access (although I did try pinging - the IP of the windows laptop works, but nothing else does).

---

### Post by gameguy on 2012-01-06
Turns out that on 11.10, I just needed to follow the instructions here:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

However, I couldn't get it to start on startup

I am using 64 bit, if it helps.
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

PS. I can start it at each boot using the commands
```

sudo insmod <path-to unpacked-tar>/wl.ko

```
In my case I moved the path to ~/.wless/wl.ko

If someone knows how to run code with elevated privelages at boot time it would be greatly appreciated.
Thanks

---

