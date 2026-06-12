---
title: "No Sound after clean install of Ubuntu 10.04"
date: 2010-05-24
forum: Multimedia Software
---

### Post by Kerubu on 2010-05-24
Hi,

I've just done a clean install of Ubuntu 10.04 after using 8.10 for a couple of years. (I have to say that after 2 years, the problems I encountered when first installing 8.10 remain in 10,04 but now with additional sound problems !)

I use an Acer Aspire 5720 and sound *WORKED* under 8.10 fine.

Now I have done a clean install of 10.04 all I get are the bongos at the login then nothing. I can't play any sound files etc. The card is recognised but something is wrong. Here are the results of some commands I have given :

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

I've checked all the mixer levels but please note as I said above... I GET THE BONGOS AT LOGIN

Can anyone help, I've noticed a few people have this problem with 10.04

---

### Post by Kerubu on 2010-05-24
Actually I got a fix by following this solution :

[http://ubuntuforums.org/showpost.php?p=9249804&postcount=3]("http://ubuntuforums.org/showpost.php?p=9249804&postcount=3")

Hmmm pulse audio STILL playing up in 10.04

---

### Post by Yellow Pasque on 2010-05-24
Please mark solved.

---

