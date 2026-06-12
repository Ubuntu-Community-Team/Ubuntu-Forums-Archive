---
title: "How I solved my wi-fi connections problems"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by Nuitblanche on 2013-02-17
Hello, I had been having wi-fi connection problems for months now - dropping, reconnecting asking for passwords or not connecting at all depending on which network I'm trying to connect to. Apparently, many people are having similar problems with 12.04 LTS.

Well, I sought all sorts of solutions. But it never occured to me that the problem was coming from the proprietary Broadcom STA driver that was installed.

On the suggestion of answer given on one of the sites:

1. "sudo apt-get purge bcmwl-kernel-source" 

and then 

2. "sudo apt-get install firmware-b43-installer b43-fwcutter"

What I did was:

1. --> "sudo apt-get purge bcmwl-kernel-source" 

2. --> "sudo apt-get auto remove" (instructions given by the terminal that followed to get rid of some unnecessary linux-headers that were auto installed)
3. --> instead of doing "sudo apt-get install firmware-b43-installer b43-fwcutter", I simply powered down the computer. Then started it again.

And VOILA - my laptop was connected SOLID BARS showing. No issues for 30 minutes now. Which is a record breaker.

It is running smoothly with whatever Ubuntu has as default wireless driver.

The problem was coming from the proprietary Broadcom STA driver that was installed.

I hope this helps others who are having the same problems.

---

### Post by Hadaka on 2013-02-17
Hi, in case you want to see what drivers you are currently using...do

```
lspci -nnk | grep -iA3 net 
```

---

