---
title: "Kernel panic Intel wireless 4965 and 3945 chipset"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by rstoya05-lx on 2008-12-04
I experience kernel panics similar to this issue:
[https://bugs.launchpad.net/276990](https://bugs.launchpad.net/276990)

In the 8.10 release notes this is described as an issue with Intel wireless 4965. This is the what I have:

```
$ lspci | grep -i wire
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

What I'd like to know is if based on my chipset I could be affected by the exact same issue? Or does this require filing a new bug?

---

### Post by Siruso on 2008-12-04
I'm having the exact same problem with my 3945abg.  No idea how to fix it, just thought I'd chime in.

Siruso

---

### Post by drcnoib on 2009-02-02
Bump!

I am still experiencing that and would love to use wireless on my computer. Any suggestions?

Using Kubuntu 8.10, all kernels available experience the same problems with the N network I have in the lab: Kernel Panic.

Do you think I should file a bug?


Catalin

---

### Post by dfnwpofb on 2009-02-18
I moved to Ubuntu from Windows recently.

Every half an hour or so the system hangs, kernel panic. This is caused, I think, by my Intel Wireless/Pro 4965 NIC.

This is a very popular network card in laptops and I am surprised that the supposedly best/most popular Linux distro cant handle it. even opensolaris can handle it no probs so why not ubuntu? I think from other posts i have seen that this whole family of cards is affected.

Is there a fix, or shall I move back to a stable os (windows /sigh)

---

### Post by 00arthuryu on 2009-05-29
Did anyone get a solution with this?
:(
I'm trying to upgrade to 9.04 at the moment

---

