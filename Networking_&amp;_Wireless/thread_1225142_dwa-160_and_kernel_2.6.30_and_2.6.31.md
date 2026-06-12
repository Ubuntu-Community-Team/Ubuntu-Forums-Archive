---
title: "dwa-160 and kernel 2.6.30 and 2.6.31"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by raqua1 on 2009-07-28
Hello.

I recently purchased D-Link DWA-160 usb dongle. It is revision A1 which uses Atheros AR9170 chipset.
I use Ubuntu 9.04. New drivers for AR9170 should be included in kernel 2.6.30 and above, so I updated my kernel to version 2.6.30.3 which I found packages for here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

My wifi still does not work. I tried to modprobe ar9170 or ar9170usb but got message that module was not found. 
When searching for 9170 on my system, some references were found in kernel-headers, but no driver. 

I also tried the same procedure with latest 2.6.31 kernel from the same source with the same result. 

Am I missing something obvious here? Where is the driver?

---

### Post by raqua1 on 2009-07-30
bump

---

### Post by jaypeesmith on 2009-08-17
I have one of these on order (it's a refurb so, I don't know which revision it is). 

However, I was looking up info on this a came across this post and it referenced a revision A card.  I am wondering if you might be missing the needed firmware.

[http://linux.com/community/blogs/Setting-up-wireless-with-ar9170-in-Linux.html](http://linux.com/community/blogs/Setting-up-wireless-with-ar9170-in-Linux.html)

There is a typo in the post.  The first comment contains the corrected text for the second firmware download.

Hope this helps.

---

