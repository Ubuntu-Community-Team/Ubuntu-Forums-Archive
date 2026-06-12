---
title: "no wired connection, lspci shows no ethernet controller"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by NewbuntuUser777 on 2011-07-31
I have no ethernet connection, I've tried updates and different distros.

lspci shows the wireless controller (which works), but nothing for ethernet

The laptop is HP Probook 4525, which has a Realtek Ethernet Integrated Controller.

---

### Post by Kooothor on 2011-07-31
Hello,
Have you tried changing the ethernet cables ?

---

### Post by NewbuntuUser777 on 2011-07-31
Yes, different cables which can connect another machine.

I did have it working at one point, but installed opensuse and then had the problems.  

Fresh reinstall of ubuntu didn't fix.

---

### Post by Kooothor on 2011-08-01
That's weird, generally ppl have troubles with wifi, no ethernet !
Try to be sure the correct modules are loaded into the kernel.

man modprobe

---

### Post by NewbuntuUser777 on 2011-08-01
At this point, I'm worried that it may be a hardware failure, but the only way I know to diagnose as such is to reinstall the hp recovery crap/win 7, which I'd rather not do since it's a huge pita.

Is there a way to diagnose such in linux?

Searching the internet turns up scads of information about wireless issues, but nothing for ethernet where the controller isn't listed by lspci.  Without information I'm a bit lost.

---

### Post by NewbuntuUser777 on 2011-08-01
bump

---

### Post by varunendra on 2011-08-02
> **NewbuntuUser777 said:**
> At this point, I'm worried that it may be a hardware failure, but the only way I know to diagnose as such is to reinstall the hp recovery crap/win 7, which I'd rather not do since it's a huge pita.

Is there a way to diagnose such in linux?
Post outputs of these:
```
ifconfig -a
```
(to see if there's just a configuration issue)
```
sudo lshw -C network
```
(to see if it's even detected or not, and if detected, then relative info)

---

