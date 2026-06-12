---
title: "Erratic wireless (Broadcom BCM4328)"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by kencamargo on 2013-01-31
Hello all,
I have Ubuntu 12.10 64 bits kernel 3.5.0-22 running on a Dell Precision M6700. The wireless controller is a Broadcom BCM43228(802.11abgn, the router also is 802.11abgn); it didn't install on a fresh install, so I added the bcmwl-kernel-source package and I got the wireless network working... sort of.  
This is a dual boot machine, and  under the same conditions that the connection running windows is stable, running Linux it is anything but; every now and then it disconnects itself, it doesn't manage to connect on its own to the router, requiring a repeater (which is not necessary with windows) and even then there are times when it connects to the network without really working (e.g. pinging the router itself returns "unreachable"). Sometimes when reconnecting it asks the network password again. At times it doesn't manage to connect at all, even with the repeater turned on. Things only really work if I am  practically stuck to the router, but that sort of defeats the whole idea of wireless connections...
Should I try the ndiswrapper?
(just during the short time  it took to compose this message the  network connected and disconnected four times and the last one is taking  a long time to reconnect, I am waiting the  reconnection in order to send this - I had to stand beside the router to be able to send it...)
Thanks for any help,
Ken

---

### Post by kencamargo on 2013-01-31
Addendum: just upgraded the kernel, and the problem persists...
I'm attaching a  variety of diagnostics, hoping someone can  make sense of this...

---

### Post by Hadaka on 2013-01-31
Hi, same card and situation as you.
[http://ubuntuforums.org/showthread.php?t=2084508&highlight=BCM43228](http://ubuntuforums.org/showthread.php?t=2084508&highlight=BCM43228)

hope this helps.

---

### Post by kencamargo on 2013-02-01
> **Hadaka said:**
> Hi, same card and situation as you.
[http://ubuntuforums.org/showthread.php?t=2084508&highlight=BCM43228](http://ubuntuforums.org/showthread.php?t=2084508&highlight=BCM43228)

hope this helps.

Hello,

Thanks, yes, same card,  but no, not the same  situation. I already got the driver installed and it works, except when  the signal is attenuated, whereas under  the same  conditions things are OK under Windows.

Ken

---

### Post by praseodym on 2013-02-01
Try a fixed channel between 1-11 and WPA2-AES (CCMP) encryption.

---

### Post by Hadaka on 2013-02-01
Hi, did you do..
```
sudo apt-get install linux-headers-generic 
```
and then reload the drver?

---

### Post by kencamargo on 2013-02-01
> **praseodym said:**
> Try a fixed channel between 1-11 and WPA2-AES (CCMP) encryption.

I'm already using WPA2, gonna check the  fixed channel. But again, under Windows I have no problems.

Thanks,
Ken

---

### Post by kencamargo on 2013-02-01
> **Hadaka said:**
> Hi, did you do..
```
sudo apt-get install linux-headers-generic 
```and then reload the drver?

I got a new kernel as of yesterday, so that was done again, automatically.

Please  note that the wireless connection works well as long as I'm relatively close to the router.

Thanks,
Ken

---

