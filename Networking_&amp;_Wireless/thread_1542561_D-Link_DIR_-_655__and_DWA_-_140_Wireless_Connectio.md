---
title: "D-Link DIR - 655  and DWA - 140 Wireless Connection Issues"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by arewethereyet on 2010-07-30
Hi all, sorry if I am beating a dead horse here. I have been searching around the net today and found various possible fixes to my problem but haven't' found one to work yet.

I have a D-Link 655 Router, a DWA 140 adapter, and am using Ubuntu 10.04 LTS.

Like I have seen expressed before, I can connect wired no problem, I can see all my neighbors wireless connections no problem, but my DIR-655 does not show up in my Ubuntu network manager, nor my Wicd manager.

When trying to connect manually using the "find hidden network" function it just loops around asking for a password.

So I'm just wondering if anyone has any specific experience trying to use these two devices with ubuntu 10.04. With the wired connection being removed from my house, and my wireless gear brand new, I will have to revert back to windows if I can't get this to work somehow. I'm really hoping to convert to Linux completely :p

Thanks in advance!

---

### Post by arewethereyet on 2010-07-30
I have gotten this Router to appear in the wireless network list by removing security.

Using Wicd I can get as far in the connection phase as "obtaining IP" then it disconnects and says "unable to obtain ip".

---

### Post by Talon2 on 2010-07-30
First try installing this:

System > Administration > Snaptic Package Manager > ...

... linux-backports-modules-wireless-lucid-generic

If the above doesn't work then there is good information in this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

---

### Post by arewethereyet on 2010-08-02
Thanks for the help ^.^

After a few days of working on this I finally got it to work and even use encription. However I could not get N mode to work, because my Ubuntu 10.04/drivers would not support AES, which appears to be required for N mode.

I'm going to return this D-Link stuff tomorrow. I'm looking around for opinions on the best wireless equipment for Ubuntu 10.04 that is 100% operational out-of-the-box, if you have any suggestions.

Thanks again!

---

