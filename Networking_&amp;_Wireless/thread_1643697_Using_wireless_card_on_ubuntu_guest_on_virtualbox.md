---
title: "Using wireless card on ubuntu guest on virtualbox"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by lordmonkeyu on 2010-12-12
hello,
Anyone heard how it can be done to use your wireless card on ubuntu guest on virtualbox ?

---

### Post by snowpine on 2010-12-12
The entire point of virtualbox is that the guest OS "sees" only the virtual hardware, not your actual physical hardware.

If wireless is correctly configured in your host OS, then the Ubuntu guest OS should "see" it as a simple wired ethernet connection. In other words it should work "out of the box."

If you are having trouble configuring your network, please be specific (hardware, host OS, exact error messages, etc) and I will try to help.

---

### Post by lordmonkeyu on 2010-12-12
Ok , but is it possible to for example possible to see wireless networks from my ubuntu guest not as a wired ?
host os : win7

---

### Post by snowpine on 2010-12-12
Connect to the wireless network in the host OS (Win7).

---

### Post by lordmonkeyu on 2010-12-12
Ok, but what if I would like to use some tools on ubuntu concerning wireless networks ?

---

### Post by snowpine on 2010-12-12
> **lordmonkeyu said:**
> Ok, but what if I would like to use some tools on ubuntu concerning wireless networks ?

Install Ubuntu on its own partition as a "dual boot" with Windows.

---

### Post by lordmonkeyu on 2010-12-12
yeah... I was trying to omit that and do it on my virtual machine but as I see I think there is no such option...

---

