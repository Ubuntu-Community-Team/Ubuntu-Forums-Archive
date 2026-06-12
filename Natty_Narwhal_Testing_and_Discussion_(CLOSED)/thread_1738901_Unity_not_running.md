---
title: "Unity not running"
date: 2011-04-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by arpit22x on 2011-04-25
Hi,

I've recently upgraded to Ubuntu Natty on Dell Inspiron 1545. But Unity is not running. I think, it's a hardware issue. Can Unity be run on my system? Please help. I have no additional graphic card but this integrated graphics.

'info.vendor = 'Intel Corporation'
  pci.product = 'Mobile 4 Series Chipset Integrated Graphics Controller''


Any help will be appreciated.

---

### Post by KegHead on 2011-04-25
Hi!

Have you selected via:

system..admin..login?

Select your default.

Restart.

Advise.

KegHead

---

### Post by coffeecat on 2011-04-25
> **arpit22x said:**
> I've recently upgraded to Ubuntu Natty on Dell Inspiron 1545. But Unity is not running. I think, it's a hardware issue. Can Unity be run on my system? Please help. I have no additional graphic card but this integrated graphics.

'info.vendor = 'Intel Corporation'
  pci.product = 'Mobile 4 Series Chipset Integrated Graphics Controller''

It's unlikely to be a graphics hardware issue. I'm posting from Natty Unity on my Sony laptop - running just fine - with:

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```That looks like the same as yours. What exactly do you get with 'lspci | grep VGA'?

---

### Post by arpit22x on 2011-04-25
Thanx for the reply, It's working as 'KegHead' suggested. :) Thanx again.

---

### Post by KegHead on 2011-04-25
Hi!

Cool & congrats!

Please mark you thread as "solved".

KegHead

---

