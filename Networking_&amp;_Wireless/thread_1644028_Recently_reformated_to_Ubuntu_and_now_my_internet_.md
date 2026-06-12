---
title: "Recently reformated to Ubuntu and now my internet disconnects"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by Hundred on 2010-12-12
Hi guys,

I was using Windows XP and my internet worked fine, then i had a few unrelated problems so i decided to reformat my PC and use Ubuntu. Now, my internet disconnects every 5 minutes randomly. Is there something i need to do to the network settings to prevent this? By the way, i am new to Ubuntu so please try keep it simple.
[I]
Note: I reformatted while the router was still connected but i've gone through the settings on the router and they seem normal[/I]

Thanks in advance,

Hundred

---

### Post by fwin on 2010-12-12
Hi there,

Im having a similar issue and I posted the following thread:

[http://ubuntuforums.org/showthread.php?t=1644053](http://ubuntuforums.org/showthread.php?t=1644053)

If you have a realtek wireless controller you may want to follow my thread. If you want to know what network controller you have, you can enter this command in the terminal:

lspci

then look for the network controller in my case it looks like this:

0a:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

Also let us know what version of ubuntu you are using 10.04 or 10.10 , 64 bit or 32bit?

good luck!

---

