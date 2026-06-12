---
title: "Stuck in update-initramfs loop."
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by SuperTeece on 2010-11-21
System: Ubuntu Server 10.10
NIC: wmp300n

Issue: Installing bcmwl-kernel-source fails - stalls at following:

```
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic-pae
```

Initially I was on this step while accessing the server using SSH on my wireles laptop. While waiting on this step to complete I lost wifi connection so I attempted to install the package again and was greeted with:

```
~$ sudo apt-get install bcmwl-kernel-source
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

I run that and get:

```
~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.98.1ubuntu6) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic-pae
```

So I moved on and run

```
sudo apt-get update
```

and again see

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

I'm stuck in a loop. Any ideas?

TC

---

### Post by SuperTeece on 2010-11-21
Forty-one views and no replies.. does that mean this is a complex issue or that I'm asking it the wrong way or in the wrong forum?

---

### Post by rburkhardt on 2011-01-29
I am having the same problem and can't find the answer either. did you ever have any luck?

---

### Post by SuperTeece on 2011-01-29
I feel bad now because I did fix it but don't remember how.

At the same time though, the wifi card still doesn't work.

Sorry.

> **rburkhardt said:**
> I am having the same problem and can't find the answer either. did you ever have any luck?

---

### Post by rburkhardt on 2011-01-31
do you remember where you might have found the solution? what brand is the wifi card?

---

### Post by rburkhardt on 2011-01-31
I disabled the built in Ethernet card and it want right throught the process no problem

---

