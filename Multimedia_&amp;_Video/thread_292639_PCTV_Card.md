---
title: "PCTV Card"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by HanaD on 2006-11-04
Hi friends,
i brought a tv tuner card - PCTV 
but i have got windows drivers for the same..
how do i make it work in Xubuntu edgy?

Please help..

Thanks

Hana

---

### Post by StormNet on 2006-11-04
Which TV tuner card do you have??

---

### Post by HanaD on 2006-11-05
The card is Pinnacle plus v5.5

[www.pinnaclesys.com](www.pinnaclesys.com).

---

### Post by HanaD on 2006-11-07
hello????

Anyonne know how to install the pinnacle PCTV card???

---

### Post by Asdmaster on 2006-11-12
usually the pinnacle tv cards use bttv modules.

install tvtime and then load the bttv modules:

```
 sudo modprobe bttv 
```

launch tvtime and see if it works...

good luck :D

---

### Post by HanaD on 2006-11-29
i can see one channel, but neither picture is clear and there is no sound, i mean its all disturbance and nothing else, can anyone please suggest a solution..

before i could only see blue screen but now atleast something is visible

---

### Post by StefanoCole on 2006-11-30
Hello, maybe the following link can help you: [http://www.linuxtv.org/wiki/index.php/Main_Page]("http://www.linuxtv.org/wiki/index.php/Main_Page")

Stefano

---

### Post by HanaD on 2007-12-30
Till Now i have tried everything i could get my hands on, but no success, even the company does not make any linux drivers for PCTV, do not think it would work..

---

