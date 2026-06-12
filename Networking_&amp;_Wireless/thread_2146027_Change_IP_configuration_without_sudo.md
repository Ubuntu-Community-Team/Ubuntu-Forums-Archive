---
title: "Change IP configuration without sudo"
date: 2013-05-17
forum: Networking &amp; Wireless
---

### Post by nignasi on 2013-05-17
We have a network laboratory with several PCs connected to Internet with DHCP. We would like to develop some experiments where PCs are connected to  switches and routers (without Internet connection) using private static IPs. After finishing the exercise PCs will use again dynamic addresses. We don't know how to allow our students to change IP configuration without administration permission. Is it possible?

We are considering some other possibilities, could you tell what do you think?

1- Two or more networks card in each PC. One managed only by root and the others managed with regular user rights. Could it be? 

2- Several system images (one for regular work others for experiments) so the student can select which one to load from a GRUB (or similar) menu. 

3- Could be possible to fix network administration rights during `login`? This way we can define users according to each experiment.

Any other idea will be welcome.

Ignasi

---

### Post by albandy on 2013-05-17
I think you should use virtual machines to do this stuff.

---

