---
title: "Connecting a 2nd laptop thru wireless link."
date: 2006-04-16
forum: Networking &amp; Wireless
---

### Post by aum11 on 2006-04-16
I do not know where to start to connect another laptop into mine.

My laptop is connected to the internet through wireless  from the house next door.  And I wish to connect another laptop through mine( this second laptop does not have wireless).

How to do this please.

Thanks.:-k

---

### Post by souki on 2006-04-16
short answer,

you can link the two laptops with ethernet (via a hub/switch, or directly with a cross cable)
then you will have to setup "internet sharing" on the wifi connected laptop

you can also do that with usb or firewire but the first solution is better

---

### Post by aum11 on 2006-04-16
Thanks Souki.

Yes I am using a crossover cable between the 2 lappies.


As for "internet sharing", how is this done?  That is the heart of my question.

I have tried using firestarter option to enable "internet sharing" through ETH0, however it says "device eth0 is not ready'.

Any suggestions.  I am very new to this lan business.

---

### Post by souki on 2006-04-16
[QUOTE=aum11]Thanks Souki.

Yes I am using a crossover cable between the 2 lappies.


As for "internet sharing", how is this done?  That is the heart of my question.

I have tried using firestarter option to enable "internet sharing" through ETH0, however it says "device eth0 is not ready'.

Any suggestions.  I am very new to this lan business.[/QUOTE]

well, I don't know about firestarter, I've allways done my setup with configuration files and scripts

you have to setup a Network Adresse Translation (NAT or masquerading)
I know a tutorial but in french here [http://doc.ubuntu-fr.org/applications/configurer_son_reseau_local](http://doc.ubuntu-fr.org/applications/configurer_son_reseau_local)

search the forum for "internet sharing" or "masquerading"
I've found one but not tested it : [http://ubuntuforums.org/showthread.php?t=91370&highlight=internet+sharing](http://ubuntuforums.org/showthread.php?t=91370&highlight=internet+sharing)

PS: for your firestarter problem, I think you have to setup static ips on ethernet interfaces (both laptops)

---

