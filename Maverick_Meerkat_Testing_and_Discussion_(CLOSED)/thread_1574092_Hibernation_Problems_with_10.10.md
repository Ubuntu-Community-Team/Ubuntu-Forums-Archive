---
title: "Hibernation Problems with 10.10"
date: 2010-09-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ATA0311 on 2010-09-13
When I close the lid of my netbook, it fails to hibernate and then when I  plug it in or unplug it, the netbook will go into hibernation. Can  anyone help me? I have asked for help before but noone has been able to lead me in the right direction.

---

### Post by cariboo on 2010-09-13
You need to give us a lot more information if you want any help. What are you running unity on? How have you got your preferences  in power management set? What have you done to try and solve the problem, aside from creating another thread saying UNE sucks?

Here'a screenshot of how I have my preferences set.

---

### Post by ranch hand on 2010-09-13
Completely OT but that screen shot looks great.  Wish it would run on my box.  That is really looking nice.

---

### Post by cariboo on 2010-09-13
Thanks ranch hand.

---

### Post by ktp on 2010-09-13
> **ranch hand said:**
> Completely OT but that screen shot looks great.  Wish it would run on my box.  That is really looking nice.

[COLOR="Silver"]OT: time to get nvidia card =)[/COLOR]

---

### Post by cariboo on 2010-09-13
My netbook runs the Intel i945 graphics chipset. :)

---

### Post by kansasnoob on 2010-09-13
I'm wondering if we should have the OP check SWAP?

That's always one of the first things I check if having trouble with suspend or hibernate.

Maybe begin by just running the command:

```
free
```

But I also always like to check that SWAP is "on" upon reboot using gparted.

All that said my vision is too poor to use a netbook :D

---

### Post by cariboo on 2010-09-14
To small a swap partition could very well be a problem, My netbook has 1Gb ram, and I created a 2Gb swap partition, I haven't had a problem with suspend and hibernate since I've owned it. I can't say how it worked in Windows, as it only lasted long enough to create a backup, and then the system was re-partitioned and formated ready for testing installs.

---

