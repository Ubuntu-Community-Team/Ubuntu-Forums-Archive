---
title: "Need help installing IPW 3945 + 802.11 Subsystem"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by jdpc_luke on 2006-07-12
Hi!, I'm new to Ubuntu, and I've been having trouble installing the Subsystem and the driver. The wireless works under a default install or from the Live CD, but when I change my kernal to the 686 to support my Core Duo, I lose wireless. Does anyone have a step by step guide to installing the 802.11 subsystem and the wireless driver? The readme's are a bit sparse.

Thanks!

If you need error messages, or anything of the sort, let me know. I'm also available over IM if someone wishes to help me that way!

Thanks! (again)

---

### Post by jdpc_luke on 2006-07-12
Another question I have is why did my wireless work on a fresh install, and after I changed the linux-image to 686 then it disappeared?

---

### Post by Ivan Wagner on 2007-02-12
I'm having the same problem. I own a Dell Inspiron 640m and on the fresh install the IPW 3945 was working smoothly using WPA and everything... Now I upgraded to Kernel 2.6.17 and my eth1 (on ipconfig) is not visible anymore.
Can anyone help me out with this problem?

Cheers.

---

### Post by Orion2000za on 2007-02-12
I can add my voice to this. I installed the new kernel and it does not "see" my wireless IPW 3945, works fine on old/default kernel (kubuntu  Edgy in my case).

I have found this page for the drivers;
[http://tinyurl.com/2xwpdw](http://tinyurl.com/2xwpdw)

not yet tested myself though. 

Sinclair

---

### Post by Orion2000za on 2007-02-13
For me at least the problem was/is solved by installing linux-restricted modules for the new kernel, a bit silly it was not indicated as in need of upgrade. I am sure it will help you who updated as it did for me

for the new user; check you have "restricted modules" for your new kernel installed, search for it in Synaptic or Adept. 

Sinclair :KS

---

