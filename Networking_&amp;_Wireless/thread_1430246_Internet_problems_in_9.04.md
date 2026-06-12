---
title: "Internet problems in 9.04"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by goddammit on 2010-03-15
Hello all...

I have an interesting problem, and it seems there are quite a few variants of this problem floating around. I am running Ubuntu 9.04 32bit on a dual boot (XP) computer. No internet problems in windows, and I am currently typing this post on my wifes HP laptop running 9.10. I have no browsing ability on the desktop running 9.04, and updates don't work (in details, every other line fails) But, I can bring up Google, and search it, pictures and all, but cannot go to different sites (ebay, hotmail, amazon as the first few i try). Also, my pidgin works fine, as I am talking on it now. I have tried to turn off ipv6 in Firefox and ubuntu, neither doing anything noticeable. any help would be greatly appreciated. i recently got rid of my laptop running ubuntu and upgraded my desktop(sparsely)  running an asrock board with integrated ethernet (not the problem, i also tried a usb wireless card with the same results) a 2.8 x64 processor, nvidia 8500 512, with 2gb of ram. nothing spectacular, but more than enough to run linux i would think. i've tried a few things from different posts, but nothing has worked yet, so maybe if i can feed more specific information, we can get my computer up and surfing again, Thanks

---

### Post by dineshs on 2010-03-15
Did you try different DNS?What is in this file?
```
cat /etc/resolv.conf
```
For google DNS,tis link may help
[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

---

