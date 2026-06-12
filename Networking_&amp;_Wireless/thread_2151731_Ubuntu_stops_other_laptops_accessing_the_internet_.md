---
title: "Ubuntu stops other laptops accessing the internet on the same network!!"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by Danzman1991 on 2013-06-05
Hi guys,

Basically, there are 3 laptops in the household. One running Ubuntu, two running Windows 8. When the laptop running Ubuntu is turned **on **it stops the laptops with Windows 8 being able to access the internet. When the laptop running Ubuntu is turned **off **the laptops with Windows 8 are able to access the internet absolutely fine! 

It is SO frustrating!

Anyone have any idea why this is happening? Would be really grateful for some help! :) 

The router is a BT Homehub 3.0 if that has anything to do with it!

Dan.

---

### Post by newbie-user on 2013-06-05
Are you running any services on the Ubuntu laptop, like DHCP?

---

### Post by Danzman1991 on 2013-06-05
> **newbie-user said:**
> Are you running any services on the Ubuntu laptop, like DHCP?How would I know that? :S

---

### Post by sky5564 on 2013-06-05
Best thing to do with windows 8 is just remove it, That's what i did and replace it with either ubuntu or linux mint.

I had nothing but problems with windows.

---

### Post by Danzman1991 on 2013-06-06
> **sky5564 said:**
> Best thing to do with windows 8 is just remove it, That's what i did and replace it with either ubuntu or linux mint.

I had nothing but problems with windows.

Quite ironic that it's Ubuntu that's causing my problem then!

---

### Post by matt_symes on 2013-06-06
Hi

Does your laptop have a broadcom wireless chip ? Is it using the wl driver ?

Post the output of

```
lspci -nnk | grep -iA2 net
```

Kind regards

---

