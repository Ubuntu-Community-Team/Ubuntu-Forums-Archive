---
title: "Ubuntu 10.10 A3 guest on Mac host using VB 3.2.8 has issue."
date: 2010-08-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by GARoss on 2010-08-18
This probably isn't a big deal & one can't expect Alpha level OS to be perfect but I thought it best to post this.

I just updated to VB v3.2.8 64453 on Mac Host & proceeded to update Guest Additions on Ubuntu 10.04, 10.10 Alpha 3 & Windows XP. My procedure is to always check for system updates first, then update Guest Additions. At the moment I'm 2 for 3. Ubuntu 10.04 LTS & Windows XP Home Edition had no issues but Ubuntu 10.10 Alpha 3 does. It seems I can no longer get a full screen but the mouse moves freely between Ubuntu 10.10 & Mac; so it is partially working. As I said, 10.04 LTS & XP are fine. I tried re-installing Guest Additions & checked for other system updates but everything is up to date.

I'm guessing the next system update will resolve the issue but how can this be checked to determine the core of the problem?

Thanks.

---

### Post by cariboo on 2010-08-18
Vbox ose was updated to 3.8.2 this morning, I get the same thing, the mouse pointer is there, and works the same way as yours. I haven't been able to install the guest addtions, as I haven't been able to complete an installation of the daily A3 build.

---

### Post by jfernyhough on 2010-08-18
The problem is down to the guest additions not supporting the new xorg-server 1.9. We have to wait for [s]Sun[/s] Oracle to update VB.

---

