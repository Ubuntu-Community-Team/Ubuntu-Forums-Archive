---
title: "modprobe : FATAL: Could not load /lib/modules/2.6.27-11-generic/modules.dep"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by BiynaYahu on 2009-03-12
```
modprobe : FATAL: Could not load /lib/modules/2.6.27-11-generic/modules.dep

socket: Address family not supported by protocol - make sure CONFIG_PACKET (Packet socket) and CONFIG_FILTER (Socket Filtering) are enabled in your kernel configuration!
```

when I perform the command dhclient eth0 I receive this error.

P.S. Sorry, in my haste I forgot some of the error.

---

### Post by BiynaYahu on 2009-03-15
*bump*

---

### Post by BiynaYahu on 2009-03-16
*bump*

---

### Post by APNelson.L on 2009-03-16
Is this causing you to have internet connectivity problems? I get a similar error but I can connect fine.

You may want to try modinfo dhclient and post back the results. My computer does not even see dhclient as a module though.

---

### Post by cariboo on 2009-03-16
Is there a modules.dep file located in the path indicated by the error message?

Jim

---

### Post by BiynaYahu on 2009-03-19
When I use: modinfo dhclient .  I get: modinfo: could not open /lib/modules/2.6.27-11-generic/modules.dep

No, there is no file at that location in fact the only folder contained within '/lib/modules' is '2.6.27-7-generic/'

---

### Post by BiynaYahu on 2009-03-23
*bump*

---

### Post by Bachstelze on 2009-03-23
Do this:

```
sudo depmod -a
```

Then try again.

---

### Post by BiynaYahu on 2009-03-23
> **HymnToLife said:**
> Do this:

```
sudo depmod -a
```

Then try again.

When I did the command you posted I received this error:
```
WARNING: couldn't open /lib/modules/2.6.27-11-generic: No such file or directory
FATAL: could not open /lib/modules/2.6.27-11-generic/modules.dep.temp for writing: No such file or directory

```

---

### Post by Bachstelze on 2009-03-23
Your system is *severely* messed up, the. Best think to do is to try reinstalling your kernel (and pray):

```
sudo apt-get install --reinstall linux-generic
```

---

### Post by BiynaYahu on 2009-03-23
> **HymnToLife said:**
> Your system is *severely* messed up

Yeah, I'm good at that.

---

### Post by BiynaYahu on 2009-03-23
So, I gave up and formatted my root directory (it's on it's own partition).  So, I suppose this thread is solved for all intensive purposes, but since it was such a crappy solution I'm going to refrain from setting this thread to solved.

---

### Post by tusseyd on 2010-10-11
I tried the "sudo depmod -a" that Ken Thompson recommended, and that seemed to have fixed the problem.  Thank you.

---

