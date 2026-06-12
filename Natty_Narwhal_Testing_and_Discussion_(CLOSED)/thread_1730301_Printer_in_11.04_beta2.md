---
title: "Printer in 11.04 beta2"
date: 2011-04-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Maintech on 2011-04-15
I have installed and am setting up 11.04 beta2 and have installed all updates. I tried to set up a lan printer but it doesn't work. The same settings work in 10.10 on several other computers. It is a Brother HL-2060 using a small print server. 11.04 recognizes and installs the driver but when I print the test page, nothing prints and it empties all the paper in the tray. It uses Jet Direct for connection .... which works fines in all my other Ubuntu releases.

---

### Post by uRock on 2011-04-15
Moved to Natty Narwhal Testing & Discussion.

---

### Post by Maintech on 2011-04-15
Bump

---

### Post by uRock on 2011-04-15
Please wait 24 hours before bumping.

Thanks,
uRock

---

### Post by bennachie on 2011-04-16
This is a long-standing problem - for some reason, Ubuntu, while identifying the printer corrector, picks the wrong PPD from the list. My 2140 has exactly the same problem, which was easily corrected in my case by installing hpijs and connecting via Foomatic/hpijs-pcl5 rather than Foomatic/postscript.

You may have to experiment a bit, preferably with only a few sheets of paper in the tray!

---

### Post by garvinrick4 on 2011-04-16
+1 with bennachie:
With upgraded Natty from Maverick with  Brother HL-2140 and foomatic/hpijs-pcl5e  and using HPIJS-PC.PPD driver name version 1.1 works fine. 2 clean installs of Natty have yet to get same printer working with recommended. As stated though be prepared to cancel in print queue or use short paper tray as is prone to run paper through printer rather fast while experimenting with.

---

### Post by Maintech on 2011-04-16
> **bennachie said:**
> This is a long-standing problem - for some reason, Ubuntu, while identifying the printer corrector, picks the wrong PPD from the list. My 2140 has exactly the same problem, which was easily corrected in my case by installing hpijs and connecting via Foomatic/hpijs-pcl5 rather than Foomatic/postscript.

You may have to experiment a bit, preferably with only a few sheets of paper in the tray!

This worked for me as well. Thank you for the information.

---

