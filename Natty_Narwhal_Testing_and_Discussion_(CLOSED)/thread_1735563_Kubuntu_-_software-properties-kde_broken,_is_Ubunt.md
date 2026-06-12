---
title: "Kubuntu - software-properties-kde broken, is Ubuntu having the same problem?"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by el_koraco on 2011-04-21
Filed a [bug]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/768363/") today. 

Not able to edit repositories or the preferred server in KPackageKit. The guys over at kubuntuforums have confirmed it, one person has confirmed the bug at Launchpad. 

Are you having the same problems with software-properties-gtk, or is it Kubuntu specific?

---

### Post by mc4man on 2011-04-21
> Are you having the same problems with software-properties-gtk
It (gtk) seems fine here other than double entries in the updates section

---

### Post by ankspo71 on 2011-04-21
Hi,
I think it is Kubuntu specific because I can launch "kdesudo software-properties-gtk" in Kubuntu, but not "kdesudo software-properties-kde". My error message looks like yours on the bug report. I clicked on the "affects me too" link.

---

### Post by el_koraco on 2011-04-21
True, the gtk package works. It's a possible workaround until the bug is fixed.

---

### Post by SeijiSensei on 2011-04-21
Seems to work fine on 10.10 with KDE 4.6.2 from kubuntu-ppa Maverick backports.

I just ran a complete "apt-get upgrade" on this box today, too.

---

### Post by el_koraco on 2011-04-21
Yep, it seems to affect just Natty. The problem has occured in the past, as Google points out, but will probably resolved shortly.

---

### Post by marl30 on 2011-04-21
I just checked and was unable to edit sources in KPackageKit... source edit actually didn't open for me. No such problem in Software Center and Synaptic Package Manger.

---

### Post by ivanovnegro on 2011-04-21
Yes, I discovered the problem right now.

---

### Post by marl30 on 2011-04-24
This just got fixed by an update. Natty is looking ready now. :D

---

### Post by PaulW2U on 2011-04-24
Confirmed as fixed. I never thought they'd fix it before release though.

---

### Post by ankspo71 on 2011-04-24
This is now fixed for me too.

---

### Post by VanR on 2011-04-24
Update just fixed it it seems.

---

### Post by ivanovnegro on 2011-04-24
Yeah, its fixed, ok, my conclusion, Kubuntu Natty is ready for release. :)

---

