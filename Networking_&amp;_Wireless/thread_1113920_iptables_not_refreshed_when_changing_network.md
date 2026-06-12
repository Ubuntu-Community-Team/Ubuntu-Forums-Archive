---
title: "iptables not refreshed when changing network"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by brunogirin on 2009-04-02
My laptop has been happily running Ubuntu for several years and thanks to NetworkManager, I regularly connect to the net through a variety or wired and wireless networks as well as a 3G modem.

When I booted the machine this morning, it could not connect at all even though it was showing good reception to the wireless network. I had that message when pinging the router:

bruno@nuuk:~/downloads/afros$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

Searching on Google (from another computer), I found out that it was due to an issue with iptables: running ipmasq with no parameters re-initialised the iptables and resolved the problem.

However, it looks like I now need to run ipmasq manually every time my network interface is brought up. Is there any way to automate it?

---

### Post by canadiandude007 on 2009-04-02
Hello,

I would suggest looking here for a start:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

But the command you are looking for would be:

```
sudo update-rc.d firewall defaults
```

Please realise that "firewall" above refers to a script you would create like on the example page above.  It could be another name of your choosing.

Hope that helps!

---

### Post by brunogirin on 2009-04-02
Thanks canadiandude007!

I actually found what the original problem was: ipmasq was installed as a dependency when I installed ARAnyM, which I just wanted to try out. What I've done so far is remove ARAnyM as well as ipmasq and it all works perfectly again. I will definitely have a look at the thread you suggest when I have the time as I'd be quite interested in understanding how iptables work.

---

