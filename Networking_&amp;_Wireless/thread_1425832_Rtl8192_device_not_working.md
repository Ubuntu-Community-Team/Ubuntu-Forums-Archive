---
title: "Rtl8192 device not working"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by Cygnus X-1 on 2010-03-09
Hello everyone,

I just started up my netbook (Medion Akoya E1315), and for no apparant reason, the little icon in the top-right corner (the Network Manager) says "Device not ready" in grey. So, after looking on a million forums and websites, I decided to go for a complete re-install of Ubuntu (9.10 netbook remix). I took the same driver that always worked before (RTL8192), and installed it with succes: I had wireless again!

But, of course, as these things go, after a restart of my laptop, the same problem occured. So the obvious question: What is this problem?

Here's what I did:

I downloaded the tar.gz from Realtek. I downloaded RTL8192se, untarred it and gave the "insmod" command. And that worked before.
I also downloaded WICD as an alternative to Network Manager, but that just gave no for an answer.

Now what the hell is the problem? Why doesn't this work? What can I do? 

Much obliged in advance! :-)

Tijs

---

### Post by suffice on 2010-04-23
I am also having the same issue for a samsung n210. I had gotten it working before then it just stopped a few days later.

Now I have installed Ubuntu 10.04 on it and it says 'device not ready'

I'm a little confused about the difference between 8192e and 8192se drivers.  My device is 8192 (rev01).  currently the driver installed is 8192se from the website.  The modprobe worked but the the thing just wont pickup wireless and the driver.  I hoping its not something silly like FN F6 or some hidden button.

I think tonight when I get home I'm going to just reinstall.  check all the lshw, lspci, modprobe and all the stuff from the million posts and try to get a good answer that can be used as a guide.  But ill keep on this until its solved.

---

