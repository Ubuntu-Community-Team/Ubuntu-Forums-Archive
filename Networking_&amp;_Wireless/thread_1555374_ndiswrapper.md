---
title: "ndiswrapper"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by cmw000 on 2010-08-18
Hi. I've used linux in the past, but I'm a fairly inexperienced user. 

I'm trying to install ndiswrapper and the graphical interface for it on my netbook, but I'm having some trouble figuring out which versions to download. I don't have internet access on my netbook so I'm trying to download everything onto a flash drive and transfer it over that way.  I don't understand a lot of the terminology and it's kind of holding me back. (jaunty, etc..)

What do I need to download exactly to get wireless working on my netbook?

Thanks in advance.

---

### Post by kerry_s on 2010-08-18
the latest is 10.04 lucid

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb)

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb)

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb)


**sudo dpkg -i *.deb**

to install all

---

### Post by cmw000 on 2010-08-28
Thanks- it worked.

---

