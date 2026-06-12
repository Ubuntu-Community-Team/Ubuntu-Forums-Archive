---
title: "ndiswrapper in intel64Bit"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by gnicezw on 2010-03-25
Hi, 

I've just plugged my old ubuntu 8.04 drive which used to run on an amd dual core 64 bit machine onto into my new intel duo core 64-Bit box. 

uname -a gives:

Linux aegis 2.6.24-22-generic #1 SMP mon Nov 24 19:35:06 UTC 2008 X86_64 Gnu/Linux. 

what i'm aiming to do is install the netgear wg311v3 wireless card drivers using ndiswrapper. The ubuntu box is currently offline and i've gone to [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)

for ndiswrapper. 

my question is can I download and safely install 	ndiswrapper-utils-1.9_1.54-2ubuntu1_amd64.deb or is there an intel specific package that I should be looking for?

thanks for reading.

---

### Post by chili555 on 2010-03-25
As far as I know, there are no Intel specific packages for ndiswrapper. I think you might be better off to go here: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ndiswrapper](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ndiswrapper)

Get the version that is appropriate for your kernel. I believe it might be Intrepid.

---

