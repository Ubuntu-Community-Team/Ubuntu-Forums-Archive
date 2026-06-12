---
title: "Headphone jack doesn't work ASUS u47VC laptop"
date: 2012-11-16
forum: Multimedia Software
---

### Post by Subcomfreak on 2012-11-16
Thread title says it all. I have anew ASUS u47VC and everything with linux has so far worked perfectly! Just one little thing needs to be fixed. When I put in my headphones the speakers on the computer mute (like they should), but there is nothing coming from my head phones.

I already checked and put every single volume meter to max, and made sure that everyone was un-muted. Still nothing.

I checked my sound card:

```
john@john-Ubuntu-U47VC:~$ sudo lspci | grep -i audio
[sudo] password for john: 
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)

```

Thank you in advance!!!

---

### Post by Subcomfreak on 2012-11-17
Is there any more information needed in order to solve this problem?

---

### Post by Subcomfreak on 2012-11-17
I checked my sound card's codac and found that it is a ALC270. Is there any driver or something that I could tell alsa/pulse to use for this specific card?

---

### Post by Subcomfreak on 2012-11-18
Is there any solution to this problem?

---

### Post by Subcomfreak on 2012-11-19
I ran alsa  info script:
[http://www.alsa-project.org/db/?f=82de5623cbdeeeae955cba02d7afe1a4b3fca965](http://www.alsa-project.org/db/?f=82de5623cbdeeeae955cba02d7afe1a4b3fca965)

---

### Post by Subcomfreak on 2012-11-20
I have had zero luck in the past with pulse audio and this is no exception. Uninstalled pulse, and it works.

---

### Post by Al_ on 2012-11-25
Thanks. Very helpful to know that this notebook is fully compatible with Linux. You may want to add it to the list on [http://www.linux-on-laptops.com](http://www.linux-on-laptops.com) where this model is not yet listed (which always make me worry).
Best
Al_

---

### Post by Subcomfreak on 2012-11-26
I would like to further test it before I add it to the list. But once I'm satisfied with its performance I will add it for sure!

---

