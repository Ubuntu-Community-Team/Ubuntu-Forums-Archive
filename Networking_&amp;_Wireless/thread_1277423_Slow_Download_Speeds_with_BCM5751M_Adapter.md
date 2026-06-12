---
title: "Slow Download Speeds with BCM5751M Adapter"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by PlankEyeWilly on 2009-09-28
I have an HP nc6230, and had issues with Jaunty and network transfers.  My download speeds would start around 15k and drop to about 2000bytes.  After a lot of searching I found a fix using sysctl and adding the following lines:

```
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760
```

I recently upgraded to Karmic, and ran into the same transfer speed issues, but the above fix doesn't seem to work. I have also tried disabling IPv6.

Any suggestions?

---

### Post by PlankEyeWilly on 2009-09-28
After a lot of searching I found some TCP tweaks at the following site:
[http://frankmash.blogspot.com/2005/11/sysctl-kernel-optimization.html]("http://frankmash.blogspot.com/2005/11/sysctl-kernel-optimization.html")

After applying that and rebooting, my download speeds have greatly increased.  After running a speed test @ toast.net im up to 750k.
[http://performance.toast.net/results.asp?testtype=4&loadtime=8.258]("http://performance.toast.net/results.asp?testtype=4&loadtime=8.258")

Hopefully this will help someone in the future...

---

