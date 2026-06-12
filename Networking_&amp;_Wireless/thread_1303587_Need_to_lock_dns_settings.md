---
title: "Need to lock dns settings"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by wildman4god on 2009-10-28
Is there a way to password protect the network setting in ubuntu, I have a user who wants web filtering on his kids computer and opendns looks like a good option but I need to be able to keep people from changing the dns setting so they can't by pass opendns. Also I don't what to hear one word from those who don't like web filtering, keep your opinions to your self. The client wants web filtering on ubuntu and that's what I need to deliver.

---

### Post by lotuseclat79 on 2009-10-28
> **wildman4god said:**
> Is there a way to password protect the network setting in ubuntu, I have a user who wants web filtering on his kids computer and opendns looks like a good option but I need to be able to keep people from changing the dns setting so they can't by pass opendns. Also I don't what to hear one word from those who don't like web filtering, keep your opinions to your self. The client wants web filtering on ubuntu and that's what I need to deliver.
Hi wildman4god,

Typically, /etc/resolv.conf is where the nameserver would be specified, and as far as I can tell, only root has write access.

I myself have opendns rigged into my router which is another way to do it, and the admin password for the router would be required.  Then the /etc/resolv.conf file would specify the router's internal network address as the nameserver.

Either way, whomever has access to the root password would be able to change the dns settings - i.e. root on the system has a different password than the admin (or root) account for the router.  My router runs the embedded [BusyBox](http://en.wikipedia.org/wiki/BusyBox) Linux variant, and has a nice graphic interface to make the change.

If someone with a regular user account on the Ubuntu system attempts to write edit a new dns setting, they would be prompted (by default) for the root password assuming root is still the owner of /etc/resolv.conf.

-- Tom

---

### Post by wildman4god on 2009-10-29
Thanks for your help

---

