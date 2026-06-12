---
title: "Set installed Realtek drivers permanently"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by dirtyhabanero on 2011-08-24
Hey all,

I've had some hiccups with my the wired connections on my new ASUS M5A88-M motherboard, ethernet card is a Realtek 8111E. The default drivers keep giving me an unstable connection - keeps starting and stopping. I figure it must be the drivers since the connection is fine when I boot to the windoze os. 

I went [here]("http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=fa") and downloaded the "LINUX driver for kernel 2.6.x and 2.4.x (Support x86 and x64)" file. Untarred and ran the .sh. Checked speedtest.net and the result was almost a mirror, if not better, than when I did speedtest on the windoze os. I read this thread [here]("http://ubuntuforums.org/showthread.php?t=804925") which gave me some insight.

The .sh appears to have replaced a r8169 driver with the one I downloaded, r8168. But when I restart, it reverts to the r8169 driver.

Any way I can set the r8168 to the default?

dh

---

### Post by praseodym on 2011-08-24
Blacklist the wrong one:

```
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf r8169
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by dirtyhabanero on 2011-08-24
Good, that's very good!

I ran into some strange problems when implementing the code - my computer hung - but I think this was just a carry over of what I was experiencing beforehand. 

Restarted my computer safely about 5 times now and am connected everytime - Thanks!



Also, someone [here]("http://ubuntuforums.org/showthread.php?t=1813183&page=2") states that the problem goes away when the kernel is upgraded to 2.6.39.

---

### Post by praseodym on 2011-08-24
Yes, it seems that the problem is Kernel 2.6.38. In >99% of the cases the driver **r8169** works without problems with cards of the vendor-ID **[xxxx:8168]**, but since 2.6.38 this number decreases rapidly. So, the "native" driver **r8168** has to be installed.

---

