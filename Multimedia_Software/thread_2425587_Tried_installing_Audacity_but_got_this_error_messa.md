---
title: "Tried installing Audacity but got this error message"
date: 2019-08-27
forum: Multimedia Software
---

### Post by iamtheeggman2 on 2019-08-27
I was installing via synaptic package manager which asked for root pw upon opening - any ideas? Thanks in advance.

```
W: Download is performed unsandboxed as root, as file '/root/.synaptic/tmp//tmp_sh' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)

```

---

### Post by iamtheeggman2 on 2019-08-27
it does appear to have installed audacity, was something wrong through to get the message?

---

### Post by PaulW2U on 2019-08-27
That's a bug in Synaptic that first appeared in 2015 and has yet to be fixed. It's actually a warning not an error. Packages always get installed correctly so the warning can be safely ignored.

Bug report for reference: [https://launchpad.net/bugs/1522675](https://launchpad.net/bugs/1522675)

---

### Post by iamtheeggman2 on 2019-08-28
Great,

---

