---
title: "UK Channel 5 won't play in 12.04"
date: 2012-09-10
forum: Multimedia Software
---

### Post by donnekg on 2012-09-10
Hi

I've installed Kubuntu 12.04 on two new PCs, and neither of them will play video from UK Channel 5's catchup service (channel5.com).  The odd thing is that an older install of Kubuntu 10.04 plays them fine.

I'm assuming that either there is a codec on the 10.04 PC that I'm missing on the two 12.04 ones, or that some newer version of media software somewhere in 12.04 has been crippled for patent reasons..  I've activated Medibuntu, and installed more codecs than I can shake a stick at, but still no luck.

If there is anyone here successfully viewing Channel 5 on 12.04 (ie you have a daughter who loves CSI ...), did you do/install anything specific?

Thanks.

---

### Post by davdo2004 on 2012-09-10
> **donnekg said:**
> Hi



If there is anyone here successfully viewing Channel 5 on 12.04 (ie you have a daughter who loves CSI ...), did you do/install anything specific?

Thanks.
 
Kubutu 12.04 here. Just watched the T20 cricket highlights. You do have the flash plugin installed ?

---

### Post by cottfcfan on 2012-09-11
What Browser are you using?
Do you have an addon blocking it, like Flashblock or Noscript?
Working fine here.

---

### Post by donnekg on 2012-09-12
@davdo
Yes, I can watch YouTube, iPlayer OK, though I have the same problem with Channel4.

@cottfcfan
I only have AdBlock installed, but even if it's set to ignore Channel5, it still doesn't play.  (I also have AdBlock on the 10.04 machine anyway.)

I think I must be missing a codec.  Any chance either of you could do a list of your installed packages so that I could compare with mine (dpkg -l > mypackages.txt)?

Thanks.

---

### Post by cottfcfan on 2012-09-12
Have you installed kubuntu-restricted-extras?
```
sudo apt-get install kubuntu-restricted-extras
```

---

### Post by donnekg on 2012-09-12
Yes, version 57, along with kutuntu-restricted-addons, and any other codec I thought might be useful. :-(

---

