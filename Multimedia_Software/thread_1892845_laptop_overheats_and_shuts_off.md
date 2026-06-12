---
title: "laptop overheats and shuts off"
date: 2011-12-08
forum: Multimedia Software
---

### Post by fibster on 2011-12-08
Hello,

Anyone have a problem such as this? Whenever I watch youtube or flash videos my acer aspire 5517 amd video laptop will overheat and shutoff?

It doesnt do this with windows 7 on the other half of the hard drive, so I figure it must be a kernel or something else?

Any help much appreciated.

---

### Post by nmaster on 2011-12-08
this is a common problem with the flash plugin. try this:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by Mark Phelps on 2011-12-13
You're right -- this is a problem with recent Linux kernels and their inability to properly handle CPU scaling -- resulting in the CPUs not cutting back to idle state.  This causes them to run hotter and, in some cases, hot enough to cause thermal alarms to trigger and shutdown PCs.  Laptops, which tend to run hot anyway, are especially succeptible to this bug.

---

