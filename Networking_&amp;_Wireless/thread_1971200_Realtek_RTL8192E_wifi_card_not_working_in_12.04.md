---
title: "Realtek RTL8192E wifi card not working in 12.04"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by cjbrooker on 2012-05-02
Hi,

Thought I'd post this to help anyone else having issues with this wireless card.

I have a Samsung N130 netbook with a Realtek RTL8192E wireless card.

Prior to upgrading to 12.04 I was using the drivers supplied by the Linux on My Samsung project repositories ([http://www.voria.org/forum/viewforum.php?f=3](http://www.voria.org/forum/viewforum.php?f=3)).

These worked fine as the Realtek drivers were not supported/working for previous releases.

When I upgraded to 12.04 again my wifi was not working. I had read that the Realtek drivers were now supported.

So I did the following:
Enabled the Realtek drives in the kernel:
```
sudo modprobe r8192e_pci
```
my wifi jumped to life!

However when I rebooted, no wifi again!

I then remembered that I had blacklisted the kernel drivers so that the Linux on My Samsung drivers were used. So I removed them from the blacklist file:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
and removed the entries for
```

blacklist r8192se_pci
blacklist r8192e_pci

```
which I had previously added.

Now all works well.

Hopefully this will help any one else with similar problems.

---

### Post by joe1826 on 2012-05-03
I'm having a similar problem except I had installed the realtek drivers in 11.10.  So when I upgraded that is what was active.  The wifi is extremely unstable and will frequently stop working, whereas i never had that problem in 11.10.  Also, the signal appears to be always weak even when im right next to the router.  If i disconnect from wifi or put the computer to sleep, I cannot connect reconnect to any wifi.  Any idea why this would be happening when it was working perfectly fine in 11.10?

---

