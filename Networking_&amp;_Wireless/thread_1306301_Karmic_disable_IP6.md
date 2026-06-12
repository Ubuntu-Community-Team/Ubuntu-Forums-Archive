---
title: "Karmic disable IP6"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by yeleek on 2009-10-30
Title says it all - how do I disable IP6 in Karmic please?  I don't use it, and want to disable it.

Thanks

---

### Post by gg234 on 2009-10-30
Try this [http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by yeleek on 2009-10-30
/etc/modprobe.d/aliases doesn't exist in Karmic.

I know it was not really possible to do in Jaunty unless you updated the kernel - which I didn't.  So wondering now how I do it with Karmic.

Thanks

---

### Post by Sinsemila on 2009-10-30
I have the same problem. I just updated hoping I could disable it by placing ipv6.disable=1 in the /boot/grub/menu.lst because I
remembered some people successfully disabled it in the grub file if they updated the kernal. Now that Karmic has the new Kernal I thought it should be easy to disable, but now theres the new problem that we can't edit grub anymore.
Anybody know how to disable ipv6 in the new grub file or if its evan possible? 
I used to be able to use OpenDns to solve the problem but evan that doesn't work anymore. I can only disable it inside Firefox which fixes Firefox but doesn't help anything else. This is so frustrating, especially when I load up other distributions and see that with just a click of a check box you can disable ipv6.

---

### Post by sliketymo on 2009-10-30
> **yeleek said:**
> Title says it all - how do I disable IP6 in Karmic please?  I don't use it, and want to disable it.

Thanks

You can disable ipv6 in firefox:

Type in" about:config" in the navigation bar,scroll down to "network.ipv6,enabled",right click,and toogle to disabled.

Are you having a problem related to ipv6 in some way that requires disabling it ?

---

### Post by yeleek on 2009-10-31
Hi,

Have been told default iptables install doesn't support ip6.  I don't use it so makes sense to disable it all together not just ff.

Thanks

---

### Post by eden159 on 2009-10-31
Take a look at this: [http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10](http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10)

---

### Post by yeleek on 2009-10-31
Spot on - that worked great.  Many thanks.

---

### Post by Sinsemila on 2009-10-31
> **eden159 said:**
> Take a look at this: [http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10](http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10)

Thanks, all fixed.

---

### Post by DexterLB on 2009-11-02
That's for Grub2. I have Grub Legacy and can't disable IPv6. Can you help? wget etc are very slow...

---

