---
title: "telenor huawei modem e1820 unstable"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by antonio_ing on 2010-10-02
hello everybody.
I have ubuntu 10.04 in my acer laptop and i have recently bought a huawei modem e1820 to connect to internet with the Telenor mobile company on Sweden. I live in a region where there is not much field, but it is still ok. Thanks to network manager i have setup the modem and it is able to connect, but the connection is not very stable and it quits randomly after some time (usually some minute) especially when using skype. With my macbook pro the connection is more stable and it quits after some hour. Can I improve this situation?

thanks for every suggestion

---

### Post by antonio_ing on 2010-10-03
no ideas?

---

### Post by alexfish on 2010-10-03
Telnor now have these APN values

Network Manager may only show the first one

nameMobilsurf med maxtaxa
apn value="services.telenor.se"

name Mobilt Internet
apn value="internet.telenor.se"

nameMobilt Bredband
apn value="bredband.telenor.se"


does changing the apn value have any affect (it is important to select correct APN for the Payment Plan), Also check with your Service Provider

Does the above help

Also check to see if Skype is supported with the pay plan

regards

alexfish

---

### Post by antonio_ing on 2010-10-03
stupid question. I have a mobilt bredband contract. Do you know what is the number to call to connect to the web? Network manager set by default *99# and internet.telenor.se

---

### Post by alexfish on 2010-10-03
[QUOTE=antonio_ing;9919968]Edit ------- stupid question. ------ 

?

---

### Post by antonio_ing on 2010-10-03
here I have to enter basic informations like the number, username and password. With the APN you have suggested it is not connecting with the number *99# which the wizard have setted automatically together with the APN internet.telenor.se

thanks for your help anyway

---

