---
title: "Locales"
date: 2010-06-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by philinux on 2010-06-18
Why do these even exist when I've already specified my language on install. I know I can install localepurge.

I know they're en but it's got my location as London GB. Just seems unnecessary cruft unless there's a good reason.

```
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date

```

---

### Post by andrewthomas on 2010-06-18
+1

maybe an /etc/locale.gen script

---

### Post by LKjell on 2010-06-18
[QUOTE=The installer]**Where are you?**
Select your location, so that the system can use appropriate display conventions for your country, fetch updates from sites close to you, and set the clock to the correct local time.[/QUOTE]

Assume you pick English language and pick Russia as your location. How can the system know what locate variant you want?

The only useful for locale setting is the decimal separation. And perhaps the yes and no questions. Otherwise a plain utf8 locate should be sufficient.

---

### Post by andrewthomas on 2010-06-18
> **philinux said:**
> Why do these even exist when I've already specified my language on install. I know I can install localepurge.

How about editing /var/lib/locales/supported.d/en to only leave the single locale that you desire?

---

### Post by wojox on 2010-06-20
> **philinux said:**
> Why do these even exist when I've already specified my language on install. I know I can install localepurge.

I know they're en but it's got my location as London GB. Just seems unnecessary cruft unless there's a good reason.



I always download localepurge on a fresh install. I've noticed this behavior before. 

I suppose their is know way of knowing what language your using. I would think they could somehow check the file it's stored in.

---

### Post by seeker5528 on 2010-06-21
> **LKjell said:**
> Assume you pick English language and pick Russia as your location. How can the system know what locate variant you want?

If you chose English with Russia as your location, it should be assumed that you want English with Russia as your location, in other words, the en_RU.UTF8 locale. 

> The only useful for locale setting is the decimal separation.

There is time, numeric, money, telephone, address, papersize and some other stuff that changes depending on your location.

Then if you are editing something you want the proper spelling, thesaurus, context checking type of stuff.

Later, Seeker

---

