---
title: "ATI CCC Crashes"
date: 2012-03-30
forum: Multimedia Software
---

### Post by Roach360 on 2012-03-30
Every time I hit apply, the window just closes, I assume it's crashing.

I just did a system reinstall, and am having the same problem.

Anyone know what's going on?

---

### Post by Yellow Pasque on 2012-03-30
How did you install the ATI driver? What happens when you start it from terminal?
```
sudo aticccle
```

---

### Post by zzarko on 2012-03-30
I had the same problem yesterday when I installed 12.3 from AMD's site. I first generated deb packages, and then installed them. I solved the problem by uninstalling deb packages and installing drivers directly from their archve. Why is CCC crashing when installed from deb's, and not when installed directly, I don't know.

---

### Post by Roach360 on 2012-03-30
> **Temüjin said:**
> How did you install the ATI driver? What happens when you start it from terminal?
```
sudo aticccle
```

Nothing happens!

> **zzarko said:**
> I had the same problem yesterday when I installed 12.3 from AMD's site. I first generated deb packages, and then installed them. I solved the problem by uninstalling deb packages and installing drivers directly from their archve. Why is CCC crashing when installed from deb's, and not when installed directly, I don't know.

Zzarko, can I get a walk-through from you on that?  I'm still learning debian distros.

---

### Post by zzarko on 2012-03-30
> **Roach360 said:**
> Nothing happens!
Zzarko, can I get a walk-through from you on that?  I'm still learning debian distros.
Well, if you installed fglrx from deb packages, you must first uninstall  them. If you used Additional Drivers application, deinstall them from  there. If you installed them manually (dpkg, synaptic, etc...), just  uninstall them from Synaptic (choose Completly remove). 

Restart the  computer and download AMD's drivers from their site (version 12.3 was  out a few days ago), if you didn't alread. After downloading, change permissions and run the installer:```
chmod +x amd-driver-installer-12-3-x86.x86_64.run
./amd-driver-installer-12-3-x86.x86_64.run
```Then just follow on-screen instructions (choose Install at the beginning). After another restart, you should have working drivers and CCC (at least, I did).

I hope this helps. Cheers,
Zarko

---

### Post by Roach360 on 2012-03-31
Great!  Now that works, but my settings seem to be causing an issue.

I use one small monitor in landscape, and a larger monitor in portrait.

As soon as I apply my settings and restart, it only uses the portrait monitor, without rotation, and it's just a black screen where my mouse is an X.

Suggestions?

---

