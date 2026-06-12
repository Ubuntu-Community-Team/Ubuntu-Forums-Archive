---
title: "ATi X1400 on Lucid Lynx: No Compiz"
date: 2010-05-02
forum: Multimedia Software
---

### Post by end3rkid on 2010-05-02
I've trying of getting work my compiz, but I can't. When I try to enable Normal Visual Effects I got this message "Desktop effects could not be enable", I can't another explain for this ratter than the video drivers that come with lucid, and I can't find a way to install the previous ones that were on Karmic Koala.

Anyone can give me a little help?

Thanks in advanced.

---

### Post by Tom Tiger on 2010-05-02
Same problem here, and I'm stuck,  I've got an ATI 4850 Radeon and sofar I've tried this;

- removed fglrx
- purged fglrx from the dpkg (can't remove it)

-system broke

-restarted with onboard intel (removed ati)  with intell compiz works flawlessly btw
-removed all ati stuff, purged, removed stuff by hand, rebooted, clean, no ati anymore.
-reinstalled all ati stuff through synaptic. shut down.
- reinstalled card

everything works,  hwinfo states that the proprietary driver is in use and active

but still no compiz.... 

Which is ironic.... since my other system which has an older 2400 radeon, does work with compiz, does everything, spinning cube ect except wobbly windows...

Both systems were upgrades from 9.10 to 10.04 no clean install.

I hate to say it, but I can't fix it.... yet....  I think I need to wait on a new driver.

---

### Post by altonbr on 2010-05-07
Have the same problem with ATI Mobility Radeon 5470 1GB. Work's on my desktop's nVidia GeForce 6800 256MB and my laptop's ATI Mobility Radeon X300 64MB...

---

### Post by blaeks on 2010-08-24
you should see what is supported by new fglrx/Catalyst. I am in the process right trying to enable openGL in my lynx installation with ati x1400 [thinpad z61m].
when I try to run catalyst control center it says "ati driver not in use or no ati device present".
you should consider this help page: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

### Post by cool Cpu on 2010-08-24
> **Tom Tiger said:**
> Same problem here, and I'm stuck,  I've got an ATI 4850 Radeon and sofar I've tried this;

- removed fglrx
- purged fglrx from the dpkg (can't remove it)

-system broke

-restarted with onboard intel (removed ati)  with intell compiz works flawlessly btw
-removed all ati stuff, purged, removed stuff by hand, rebooted, clean, no ati anymore.
-reinstalled all ati stuff through synaptic. shut down.
- reinstalled card

everything works,  hwinfo states that the proprietary driver is in use and active

but still no compiz.... 

Which is ironic.... since my other system which has an older 2400 radeon, does work with compiz, does everything, spinning cube ect except wobbly windows...

Both systems were upgrades from 9.10 to 10.04 no clean install.

I hate to say it, but I can't fix it.... yet....  I think I need to wait on a new driver.



i have ati 4850 it work with latest catalyst and the compiz and everything is really perfect i use ubuntu lucid

---

### Post by blaeks on 2010-08-24
> **cool Cpu said:**
> i have ati 4850 it work with latest catalyst and the compiz and everything is really perfect i use ubuntu lucid

what drivers and openGL do you use?
and do you have dual monitors? I want to extend my display to external monitor...
thanx!!!

---

