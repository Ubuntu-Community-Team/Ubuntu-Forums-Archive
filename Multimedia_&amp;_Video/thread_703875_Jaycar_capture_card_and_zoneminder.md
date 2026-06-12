---
title: "Jaycar capture card and zoneminder"
date: 2008-02-21
forum: Multimedia &amp; Video
---

### Post by SL666 on 2008-02-21
Hi Guys,

I've currently got 2 cameras mounted on my house using the software that came with the capture card, however its not flexible enough for me, i want to be able to do several things that my current setup doesn't do.

Being an ubuntu geek, i would like to run a linux based solution, Zoneminder resulted from google, im only a little way along this journey, and im getting stuck with getting the cap card working.

The capture card came from jaycar

[http://www.jaycar.com.au/productView.asp?ID=QV3080&CATID=13&keywords=&SPECIAL=&form=CAT&ProdCodeOnly=&Keyword1=&Keyword2=&pageNumber=&priceMin=&priceMax=&SUBCATID=451](http://www.jaycar.com.au/productView.asp?ID=QV3080&CATID=13&keywords=&SPECIAL=&form=CAT&ProdCodeOnly=&Keyword1=&Keyword2=&pageNumber=&priceMin=&priceMax=&SUBCATID=451)

but it appears to be the same one electus sell.

[http://www.electusdistribution.com.au/productView.asp?ID=9517&CATID=13&keywords=&SPECIAL=&form=CAT&SUBCATID=237](http://www.electusdistribution.com.au/productView.asp?ID=9517&CATID=13&keywords=&SPECIAL=&form=CAT&SUBCATID=237)

Its made by "Kguard" i believe it is either this card (or its sister)
[http://www.kguard.com.tw/en/KG_901.asp#](http://www.kguard.com.tw/en/KG_901.asp#)

I loaded ubuntu and it seems to have picked up that its based on SAA7134 chipset, but appears to be one of the cards that doesn't identify itself.

using camorama to test it, i get a scrambled picture, so using the method of 

```
rmmod saa7134_alsa
rmmod saa71234
modprobe saa7134 card=x,x,x,x
```

i have run through a lot of iterations of x (except i messed a lot up and have to go re-run them.. )

Is there a better way of identifying what driver/setting/moduleything works? or do i have have to increment through the 114+ versions?

Cheers Steve.

---

### Post by SL666 on 2008-02-22
:( have brute forced my way through all the available configurable cards none work...

Is there anothe way i can do this? or is just a matter of "it doesn't work with linux"?

---

### Post by SL666 on 2008-02-24
anyone?

I'm running Gutsy on AMD32.

---

