---
title: "Acer Aspire Wireless- Madwifi- Kernelpath Error"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by ScottyP431 on 2009-03-01
Hey,

I am trying to get my wifi to work following these instructions

[https://help.ubuntu.com/community/AspireOne#Install](https://help.ubuntu.com/community/AspireOne#Install) Ubuntu Intrepid Ibex 8.10 on the Acer Aspire One

I am to the point where it says "make"

It gives me this error /lib/modules/2.6.27-7-generic/build is missing, please set KERNELPATH. Stop.

Before I started I read on this site [http://cutec.wordpress.com/2008/08/17/acer-aspire-one-zg5-xubuntu-hardy-8041-and-atheros-wlan/](http://cutec.wordpress.com/2008/08/17/acer-aspire-one-zg5-xubuntu-hardy-8041-and-atheros-wlan/) to install build essential, which I did using the included instructions.

Thanks in advance for any help.

Edit- I found in another thread instructions for linux-headers-generic and installed them, but its still giving me the same error

---

### Post by Coldhak on 2009-08-17
I had the same problem. took me a bit, but I found the answer:
[http://ubuntuforums.org/showthread.php?t=587085](http://ubuntuforums.org/showthread.php?t=587085)
(in case that thread gets removed), the answer is that we were missing the package
sudo apt-get install linux-headers-$(uname -r)

---

