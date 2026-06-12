---
title: "Verizon CDMA UM150 not connecting."
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by Longwing on 2009-01-30
Until about two days ago, I've been able to access the internet through my Verizon Wireless UM150 USB modem on my laptop (A Dell Mini 9 with a proper, non-dell install of Ubuntu 8.10).

I'd plug the modem in, hit "Auto Mobile Broadband CDMA Connection", wait a minute, then surf happily.

Then it suddenly stopped working, for no particularly obvious reason. Now, when I plug it in and try to connect, it thinks a second, and says: "The network connection has been disconnected."

There's nothing wrong with the account, and the card works just fine on a macbook running OS 10.5 with the latest version of VZAccess Manager (Ugh), but it's flatly refusing to behave on Ubuntu. 

Any ideas? I'm completely clueless when it comes to wireless modems and linux.

---

### Post by raparks on 2009-01-31
I ran into the same problem today (01/31/2009) after installing updates... my Verizon UTStarcom UM150 VE broadband adapter would no longer work.  Some folks on another thread are saying that this is a problem with kernel 2.6.27-11.

---

### Post by CedricMordrin on 2009-02-02
I noticed this as well, with my UM150.  Reverting to the 2.6.27.9 kernel allows for the device to work again.  I tried on a co-workers Fedora 10 box w/ 2.6.27.12 and it had the same error I was seeing on mine.

We also tried his AT&T Aircard and it also did not work.

Now to search upstream bug reports.

---

### Post by CedricMordrin on 2009-02-02
> **CedricMordrin said:**
> I noticed this as well, with my UM150.  Reverting to the 2.6.27.9 kernel allows for the device to work again.  I tried on a co-workers Fedora 10 box w/ 2.6.27.12 and it had the same error I was seeing on mine.

We also tried his AT&T Aircard and it also did not work.

Now to search upstream bug reports.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322879](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322879)

---

### Post by Longwing on 2009-02-02
It's extremely heartening to know that I'm not the only one encountering the error. I guess I'll just keep an eye on the Launchpad report and hope someone comes up with a workaround.

---

### Post by CedricMordrin on 2009-02-02
> **Longwing said:**
> It's extremely heartening to know that I'm not the only one encountering the error. I guess I'll just keep an eye on the Launchpad report and hope someone comes up with a workaround.

I imagine that this is going to be dealt with upstream as it seems to be Kernel level. There is a bug submitted to redhat for Fedora as well.

---

### Post by Flyers2391 on 2009-03-06
> **Longwing said:**
> Until about two days ago, I've been able to access the internet through my Verizon Wireless UM150 USB modem on my laptop (A Dell Mini 9 with a proper, non-dell install of Ubuntu 8.10).

I'd plug the modem in, hit "Auto Mobile Broadband CDMA Connection", wait a minute, then surf happily.

Then it suddenly stopped working, for no particularly obvious reason. Now, when I plug it in and try to connect, it thinks a second, and says: "The network connection has been disconnected."

There's nothing wrong with the account, and the card works just fine on a macbook running OS 10.5 with the latest version of VZAccess Manager (Ugh), but it's flatly refusing to behave on Ubuntu. 

Any ideas? I'm completely clueless when it comes to wireless modems and linux.

I got a kernel update the other day, 2.6.27-11, and this same thing happened to me and a coworker.  This morning I had a bunch of updates, installed them and it is once again working.  I use a sprint broadband card but since I was having the same issue as you after an update I'm hoping it's an all around fix

---

