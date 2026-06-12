---
title: "D-Link DWA-140 (ra2870 chipset) in monitor mode"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Crym on 2008-12-29
Is there possible to use this card in monitor mode? If so, how would i proceed to switch modes?
(I have only used Linux for some months now, so i'm quite fresh)

Thanks,
Crym

---

### Post by Crym on 2008-12-30
/bump

---

### Post by lemmy999 on 2008-12-30
I take it you are trying to use this NIC with Aircrack?

If so try 

```
airmon-ng start rausb0
```

If successful there will be an indication that the card is now in monitor mode

---

### Post by Crym on 2008-12-30
thanks, that did it =)

but, does anyone know if it it possible to use package injection with this card/chipset? I cannot seem to get it to work. i get 0/30: 0% all the time when i try (testing on my own router that is WEP encrypted).
I'm trying to follow these guides: 
[http://www.aircrack-ng.org/doku.php?id=injection_test]("http://www.aircrack-ng.org/doku.php?id=injection_test")
and
[http://www.aircrack-ng.org/doku.php?id=simple_wep_crack]("http://www.aircrack-ng.org/doku.php?id=simple_wep_crack")

---

### Post by lemmy999 on 2008-12-31
When you try the injection test does it come back with

```
 Injection is working!
```

??

It might help if you post the output for 
```
 aireplay-ng -9 rausb0
```

---

### Post by theinnercityhippy on 2008-12-31
> **Crym said:**
> thanks, that did it =)

but, does anyone know if it it possible to use package injection with this card/chipset? I cannot seem to get it to work. i get 0/30: 0% all the time when i try (testing on my own router that is WEP encrypted).
I'm trying to follow these guides: 
[http://www.aircrack-ng.org/doku.php?id=injection_test]("http://www.aircrack-ng.org/doku.php?id=injection_test")
and
[http://www.aircrack-ng.org/doku.php?id=simple_wep_crack]("http://www.aircrack-ng.org/doku.php?id=simple_wep_crack")

I'm fairly sure that card uses the rt73 driver in ehich case packet injection should be supported. You will have to be fairly close to the source though to inject, ideally the power strength indicated by airodump-ng should be at least 103 or above to do this successfully.

Have fun

-JimDog*-

---

