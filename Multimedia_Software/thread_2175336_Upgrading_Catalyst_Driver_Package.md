---
title: "Upgrading Catalyst Driver Package"
date: 2013-09-18
forum: Multimedia Software
---

### Post by zombienerd1 on 2013-09-18
I am currently running AMD's Catalyst 12.9, and just downloaded the package for 13.8 beta, as I'm told it gives much better performance.

My question is there a special method for upgrading?  Do I have to remove the old package before installing the new one?  Any special considerations?  I am making a clonezilla backup before I install, just in case.

Plenty of websites describe installation, and I've done it before, when I installed 12.9, but nobody really mentions what to do during an upgrade.

I appreciate any input.

In case it matters, here's my specs:

Asus M3A78-CM
Phenom 9600 Quad core
8gb Ram
Sapphire AMD Radeon 7770 Ghz edition 1gb

---

### Post by QIII on 2013-09-18
Hello!

If you installed the driver using the .run from AMD/ATI before, you need to uninstall it.  It doesn't "upgrade".  If you've done it before, it's is pretty straight forward:

```
sudo amdconfig --uninstall
```
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Reboot to the opensource driver.

Download the new .run and execute it.

Then

```
sudo amdconfig --initial
```

Reboot.

Make your adjustments in CCC.

Reboot.

By the way, if you don't know this:  If you use the driver from the AMD/ATI website you should watch for kernel updates when you do your normal updates.  If there are any, don't do the updates until you uninstall the driver and then reinstall it after you have done your updates.  If you don't, the best you can hope for is no driver after you reboot.  There is a high likelihood of a big mess in the worst case.

Best wishes!

---

### Post by zombienerd1 on 2013-09-18
Thanks much for the info, that's exactly what I was looking for.  I'll keep an eye on kernel updates as well.  I've only been running Ubuntu for a few months, I'm lucky I haven't had a kernel update yet.

---

### Post by Yellow Pasque on 2013-09-18
> **zombienerd1 said:**
> I am currently running AMD's Catalyst 12.9, and just downloaded the package for 13.8 beta

You do know they released 13-9 today, right?

---

