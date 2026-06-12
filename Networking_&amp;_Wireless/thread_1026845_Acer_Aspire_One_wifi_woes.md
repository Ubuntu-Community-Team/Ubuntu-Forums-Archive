---
title: "Acer Aspire One wifi woes"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by unclejames on 2008-12-31
So, my wifi has worked just fine until a recent system update. After that, it didn't do a thing. (As a side note, this is really very irritating indeed. It's had me spending hours trying to get things to work. This smacks of a not very properly tested release to me. But still.)


I've manually installed madwifi, which - yay - sees some wifi networks, but sadly doesn't see the one I wish to connect to. Both "My Street private" and the phantom but nevertheless available "Free Public WiFi" are both invisible to my Acer.

I do have one WPA2 connection which is visible. However, attempts to connect to that also fails.

What else would people recommend to get my little Acer connecting via wifi again? It's very annoying!

---

### Post by pytheas22 on 2008-12-31
The easiest solution, if indeed this problem stems from a bad kernel update, would be simply to boot into an older kernel.  At the grub boot menu, which you should see before the big orange Ubuntu bar starts loading (you may need to press 'escape' to get into it if Ubuntu is the only operating system on your computer), you should have a list of kernels to boot into, with the most recent at the top.  Try choosing an older one; does your wireless work there?

If not, what is the output of:
```

sudo iwlist scan
```

And also do you have better luck connecting to the one network that you can see if you use [wicd]("http://wicd.sourceforge.net") to connect?

---

