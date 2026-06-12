---
title: "Driver for Atheros AR928x?"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by Flaredancer on 2010-03-19
Hey all.
I'm pretty new, so keep that in mind if you answer me.. I'm really really not good with Linux (YET! :D). I just downloaded Ubuntu Studio on my laptop and am loving it but I can't get the wireless to work.
I think it's because I need a driver; the Atheros AR928x.

Whatever the driver is, it works with the pretty unpopular Musix distribution, because wireless worked instantly when I got that. I switched because it was old and slow.

Any help obtaining and installing this driver would be greatly appreciated!

Thank you.
-Flaredancer

---

### Post by Flaredancer on 2010-03-19
I really hate bumping, but...

---

### Post by bkratz on 2010-03-20
> **Flaredancer said:**
> I really hate bumping, but...



Well I'm about to show my true level of ignorance, but at least it will bump you, and maybe someone that knows will see it.  I thought the drivers for that device were already in Unbuntu, but I could be wrong ( not the first time ). I thought they are called something like ath5k or ath9k.

Could you go to the terminal ( Applications>>Accessories>>Terminal ) and type in the following (one at a time )

```
sudo lshw -C network
lsmod
sudo iwlist scan

```

Copy/paste the outputs back here, but be sure and use the code tags (#) above to make it readable since they are really long.

 those l's above are lowercase L's not ones

---

### Post by bkratz on 2010-03-22
> **Flaredancer said:**
> 

Please see the last entry in your other posting for a good description.

[http://ubuntuforums.org/showpost.php?p=9008054&postcount=16](http://ubuntuforums.org/showpost.php?p=9008054&postcount=16)

---

