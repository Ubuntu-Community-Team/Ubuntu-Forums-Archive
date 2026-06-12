---
title: "Wireless disabled"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by samarth009 on 2009-03-24
i have a hp compaq nx6110
with a broadcom wireless adapter
m havin problems with runnig my wireless connection coz my wlan is disabled
the thing is that i have a push button for wlan on / off and not a switch .. 
i have tried pushin it before ubuntu starts but it doesnt respond . . i don hav windows .. and i don no wat to do ... 

m kinda new with ubuntu ............. soooo plzzz help:(

thanx

---

### Post by albandy on 2009-03-24
try 
sudo ifconfig wlan0 up

---

### Post by samarth009 on 2009-03-24
hey i just did that but it says 
No such file or directory

---

### Post by BillyPrefect on 2009-03-24
What model of broadcom wireless?  43xx??  Type 

lshw -C network

---

