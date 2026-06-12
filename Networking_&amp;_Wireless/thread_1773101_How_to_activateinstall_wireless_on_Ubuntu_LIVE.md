---
title: "How to activate/install wireless on Ubuntu LIVE"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by Pictor on 2011-06-01
Hello,

I'm working on an *Ubuntu Live 10.10 (Maverick)* and I'm trying to make my wireless _Broadcom_ card to work.
Installing Ubuntu on the hard disk there's no problem activating it, but unfortunately in the lately I'm working **ONLY on the Live** version (from a USB Flash drive).

Under Ubuntu Live I tried to *Activate* the "_Broadcom STA wireless driver_" but, after downloading, it returns an error saying a very few detailed error:

[B]"SystemError: installArchives() failed"
[/B] 
... and I cannot understand where is the problem or what to do to solve it.
I already tried to run "jockey-gtk" with "sudo" but it is not a permission issue. The error came out anyway.

Has anybody a solution to make my wireless card to work?

---

### Post by Pictor on 2011-06-02
Anybody know something about my problem?

I cannot understand if I'm doing something wrong or if that's a bug of Ubuntu Live.

..... even if I remember to have been able to activate the driver on Ubuntu Live, once in the past.......

---

### Post by TBABill on 2011-06-02
Normally from a LiveCD all I do is click the additional drivers and the system knows to look on the CD for the driver and firmware. I let it do its install routine, then when it says you must restart, DO NOT RESTART! Simply do a ```
sudo modprobe wl
``` and give it a few moments to begin seeing networks. I have a BCM4312 Broadcom card and this works every time. 
 
Which model is your Broadcom? You can also try ```
sudo apt-get install --reinstall bcmwl-kernel-source
``` and then click the additional drivers and install as normal, also without rebooting.
 
Edit: I'm not sure if this works exactly the same from USB, but I assume it does. I just don't know if you can add a USB device as a repo like you can a CD.

---

