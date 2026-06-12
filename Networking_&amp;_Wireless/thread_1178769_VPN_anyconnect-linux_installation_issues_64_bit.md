---
title: "VPN anyconnect-linux installation issues 64 bit"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by jake0391 on 2009-06-04
I am trying to get anyconnect-linux-2.3.0254-k9.tar.gz working so I can VPN into work. I am running on a Dell E6500. 

I am running 64 bit :
# uname -a
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

The problem first started with VPNC coming up with group password issue. Working with a co-worker who is running 32bit (and works) this looked like to be the solution. Based off this web site.

[http://koroshiyaitchy.wordpress.com/2009/05/09/using-cisco-anyconnect-vpn-client-in-unbuntu-jaunty-64-bit](http://koroshiyaitchy.wordpress.com/2009/05/09/using-cisco-anyconnect-vpn-client-in-unbuntu-jaunty-64-bit)

I am getting the following errors when I am running the install script.

/etc/init.d/vpnagentd_init: 68: /opt/cisco/vpn/bin/vpnagentd: not found

After searching it appears that I am missing a link to the library of some sort. 

Any one got any ideas???

-Tim

---

### Post by DouglasAWh on 2010-02-04
> **jake0391 said:**
> I am trying to get anyconnect-linux-2.3.0254-k9.tar.gz working so I can VPN into work. I am running on a Dell E6500. 


Is this still a problem in 2.4?

---

