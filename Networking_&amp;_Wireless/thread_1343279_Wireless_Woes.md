---
title: "Wireless Woes"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by minus_zer0 on 2009-12-01
Hi all! I'm pretty new to Ubuntu, currently using version 9.10. I am thoroughly enjoying using Ubuntu and find it a very good operating system and very fast after having used Windows for many years. The only trouble I am having is with my wireless network and as you can appreciate this is very annoying and hindering an otherwise positive experience! 

I'm using a Broadcom 4318 card which from what I have read I understand that many people have a lot of problems with this card. I have had several issues with it along the way but I am now able to connect to the network with no problems. However when I try to browse a web page in firefox it stays on "looking up" web page and doesn't move on. If however I disconnect and re-connect to the network (or sometimes just simply wait) it will allow me to use the internet. 

I'm not entirely sure where the problem lies. Could it be a DNS issue or something? Or is it just a problem with drivers etc.? I used NdisWrapper to install the windows drivers from the manufacturers website. I'm using WPA2 encryption with a static IP setup. WPA would not work at all with my card...and I'm using the standard Gnome network manager. One thing I did notice is that when I connect to an unsecured network (courtesy of my next-door neighbour!) it connects to the internet immediately with no hassle. This does suggest to me that it's an issue maybe with the encryption and my particular card but as I said I am new to Ubuntu so it could be something simple.

Any ideas would be greatly appreicated and thanks for taking the time to reply!

---

### Post by coffeecat on 2009-12-01
The fact that you're getting very slow browsing when connected to your router but things are OK when you're - ahem - hitching a ride on your neighbour's very much suggests this bug:

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757)

Post #7 is interesting and possibly relevant here.

Here's a quick test. In firefox, type 'about:config' in the address bar. Dismiss the 'here be dragons' nonsense. Type 'ipv6' in the filter to get the 'network.dns.disableIPv6' line. Change the value from false to true and restart firefox. Using your router, can you now browse OK? If so, that's only fixed firefox. You'll still get delays on other bits of the system that have to use the internet.

For a system-wide fix (if this is relevant), have a look at post #72 of the Launchpad thread for a global fix (or rather, workaround until the bug gets fixed) using grub. Or, if that doesn't work or doesn't appeal to you, try the [OpenDNS servers]("https://store.opendns.com/setup/device/ubuntu/") which seem to work for some. Although I seem to remember that on that Launchpad thread, that was dismissed as an effective fix.

**Edit:** forgot to add. Although you've managed to get wireless working with ndiswrapper, if you ever get tired of having a Windows driver on your system, have a look at [this post]("http://ubuntuforums.org/showpost.php?p=8371562&postcount=3").

---

### Post by minus_zer0 on 2009-12-01
Thanks very much for your reply...will have a nose through your links and try that out tomorrow. Will post back with results! Cheers!

---

