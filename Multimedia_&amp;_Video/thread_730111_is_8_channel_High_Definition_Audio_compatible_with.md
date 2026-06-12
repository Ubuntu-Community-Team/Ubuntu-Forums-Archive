---
title: "is 8 channel High Definition Audio compatible with ubuntu?"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by syms on 2008-03-20
hello,
i think this sound card codec is incompatible with linux, but does there will be easy to install these drivers for ubuntu? cuz im gonna buy a new motherboard, and it integrates this sound card and i want that everythink will work fine in ubuntu. and please if u have time can u take a look at this motherboards:
[http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=2281](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=2281)

[http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=2283](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=2283)

[http://tw.giga-byte.com/Products/Motherboard/Products_Overview.aspx?ProductID=2316](http://tw.giga-byte.com/Products/Motherboard/Products_Overview.aspx?ProductID=2316)

i want buy one of these three motherboards, what motherboard is most compatible with linux and does i in these motherboards possible to install xp but not vista? thanks for patience.

---

### Post by wolfen69 on 2008-03-20
after looking at those, i think they should work just fine. i also use gigabyte boards with no problems.

---

### Post by syms on 2008-03-20
> **wolfen69 said:**
> after looking at those, i think they should work just fine. i also use gigabyte boards with no problems.

thank you but how about sound? all these three motherboards have Realtek ALC883 Audio Codec, i readed that it dont works in ubuntu feisty, but maybe it works on ubuntu gutsy or hardy? and how about video? these first two motherboards have got nvidia geforce 6100 video chipset, these motherboards are very cheap and maybe this integrated video will be bad and compiz fusion will not work on them? thanks for help again

---

### Post by wolfen69 on 2008-03-20
compiz may not be blazing fast with that card, but should work. you should have no problems with sound in the upcoming Hardy Heron. many drivers have been added.

---

### Post by Ecclesia on 2008-03-20
Actually, I would be more careful with the integrated video.  I can't speak for these boards personally, but I have a board with integrated Nvidia 7150 and I needed to install drivers manually to get 3d acceleration to work.

I'd do some searching on google if I were you and not buy the boards until you know that each of these elements are compatible.  I was able to get my computer working, but it was not as pain free as I would have liked.

---

### Post by Yellow Pasque on 2008-03-21
Realtek ALC883 will definitely work if you upgrade to ALSA 1.0.16 and configure it correctly:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by syms on 2008-03-21
> **Ecclesia said:**
> Actually, I would be more careful with the integrated video.  I can't speak for these boards personally, but I have a board with integrated Nvidia 7150 and I needed to install drivers manually to get 3d acceleration to work.

I'd do some searching on google if I were you and not buy the boards until you know that each of these elements are compatible.  I was able to get my computer working, but it was not as pain free as I would have liked.

well this motherboard is currently super cheap, almost free motherboard. even geforce 6600 having higher price than this motherboard, i think i should have more search about these motherboards.

---

