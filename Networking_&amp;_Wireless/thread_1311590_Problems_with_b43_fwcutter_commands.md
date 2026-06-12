---
title: "Problems with b43 fwcutter commands"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by lawrencesmith123 on 2009-11-02
I have been going step by step in this guide;

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I just reached the point that says;

> 
[LIST=1]
[*]Obtain
[LIST]
[*][http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and
[*][http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2).
[/LIST]
 
[*]Execute the following necessary commands on the files above manually
[/LIST]

sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.obut... these directions are very vague. I placed those files on my desktop, and ran the commands in the terminal but it runs into errors. "Cannot open input file ..."

I have tried a couple things that could work but so far no luck. Things like;
-pasting the files into "lib/firmware", since they do not appear in this place. but it would not let me paste them into the file.
-changing the file address to the desktop, but this did not work either.
-I have tried reinstalling b43fwcutter, but it does not help
-many other things.

I'm guessing that im missing a crucial step, something that a new linux user would not do. Please help?

-lars

---

