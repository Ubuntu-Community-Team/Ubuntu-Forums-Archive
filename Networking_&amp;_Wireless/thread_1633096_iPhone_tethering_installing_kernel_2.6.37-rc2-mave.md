---
title: "iPhone tethering: installing kernel 2.6.37-rc2-maverick breaks iPhone tethering"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by sambhogi on 2010-11-28
I was experiencing sporadic screen racing and flicker that was making my new 10.10 installation unusable. After researching online, I installed the kernel as available here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/)

This solved my video issues completely. However, it broke iPhone tethering. Tethering was working fine in Maverick with kernel 2.6.35, after installing ipheth and ipheth-dkms. Now it isn't. 

According to the ipheth website,this driver should be compiled into the kernel by default as of 2.6.34. However, the default Maverick install required installing ipheth-dkms and ipheth-utils separately in order for tethering to work. With the 2.6.37 kernel, tethering doesn't work either way - with the ipheth packages removed or installed. 

Suggestions?

---

### Post by sambhogi on 2010-11-29
bumpkin

---

### Post by sambhogi on 2010-12-01
I can report that the fix reported here does not work for me:

[http://frankhjung.blogspot.com/2010/10/ubuntu-netbook-remix-tethering-iphone.html](http://frankhjung.blogspot.com/2010/10/ubuntu-netbook-remix-tethering-iphone.html)

I have also added the PPA to get the latest version of libimobiledevice etc. This also did not help. 

The author of ipheth seems to think the kernel alone with libimobiledevice should suffice, but clearly it does not. 

There needs to be a howto on iphone tethering/pairing that is up to date and accurate. This is a fairly common need for Ubuntu users.

---

### Post by sambhogi on 2010-12-03
When I boot 2.6.35 on my install, tethering works. When I boot 2.6.37, it doesn't. I did remove and reinstall ipheth-dkms, ipheth-utils, and gvfs, but it made no difference. I suppose I will have to write the kernel team with this or log it as a bug.

---

### Post by edgars on 2011-02-03
I am having the same problem with ipheth. Only difference is that the kernel I updated to was 2.6.38 from natty daily.

---

