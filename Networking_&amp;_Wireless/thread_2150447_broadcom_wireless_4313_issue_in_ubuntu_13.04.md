---
title: "broadcom wireless 4313 issue in ubuntu 13.04"
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by salmanbashir on 2013-06-01
Hi everybody

I have broadcom 4313 wireless card on my computer. As you all know 13.04 has issues with it. However reading a post I did the following actions:


sudo apt-get remove bcmwl-kernel-source

And installed

 [http://packages.ubuntu.com/quantal/i386/bcmwl-kernel-source/download](http://packages.ubuntu.com/quantal/i386/bcmwl-kernel-source/download)

and to block future updates to it I did

sudo gedit /etc/apt/preferences.d/bcmwl-kernel-source

After that gedit window popped up and I wrote in it and saved 

Package: bcmwl-kernel-source Pin: version 5.100.82.112+bdcom* Pin-Priority: 1001

my internet is working fine now. All I want to ask is that the steps I did for blocking future updates to the package are correct?

thanks and regards
Salman

---

