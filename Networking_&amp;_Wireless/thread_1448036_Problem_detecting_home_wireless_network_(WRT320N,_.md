---
title: "Problem detecting home wireless network (WRT320N, WUSB600N)"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by kidxcore on 2010-04-06
hello everyone.
first off, i would like to say that im a total noob and i just only today installed ubuntu 9.10 on my system (dual boot) just wanting to give it a try and see what its all about.
installation of the os and all were very fast and smooth. but now im having trouble connecting to my home network.

i am using a Linksys WUSB600N usb network adapter and my router is a Linksys WRT320N router. my home network is using WEP (40/64 bit (10 hex digits) authentication.

here's the problem:
i can see all the other networks around me but for some reason i cant see my own. i tried resetting the router so it wouldnt require any authentication but to no avail i still dont see the 'linksys'. i have no such problems on windows 7. i always was able to detect the router. this is really odd to me cos it cant be my adapter's problem cos i can see 20 other wireless networks.
is my router the cause of the problems? does ubuntu not support my router or sth?

i have also attached some screens.

please help!

---

### Post by kidxcore on 2010-04-07
help????????? :(

---

### Post by kidxcore on 2010-04-07
please?????????????????????????????????????????????

---

### Post by chili555 on 2010-04-07
Is your router set to N speeds or mixed B, G or N? Networking at N speeds is a little touchy in Linux these days and I wonder if your router is set to *_only_* communicate at N speeds when your wireless card won't yet do so, and so therefor your card won't yet see it. Just working a hunch!

---

### Post by kidxcore on 2010-04-07
hey thanks! okay i tried what u said
i changed it from mixed to G-only. now i can see my home wireless network but i cant connect to it.
it prompts for the WEP password and after i enter, nothing happens. the animation just keeps turning as though its connecting but nothing happens.

---

### Post by kidxcore on 2010-04-07
bump

---

### Post by chili555 on 2010-04-07
> it prompts for the WEP password Do you mean the WEP *key*? More specifically, the 40/128-bit HEX key? How many characters are in your key? Have you tried both upper and lower case, if there are letters in your key?

---

