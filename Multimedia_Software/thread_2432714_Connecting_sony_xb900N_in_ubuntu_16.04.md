---
title: "Connecting sony xb900N in ubuntu 16.04"
date: 2019-12-07
forum: Multimedia Software
---

### Post by amith3 on 2019-12-07
I'm not able to connect my sony xb900N bluetooth headset in ubuntu  16.04. I tried using default bluetooth manager and blueman. Both failed  to add the device. What could be the problem?
[IMG]https://i.stack.imgur.com/4V8vO.png[/IMG][IMG]https://i.stack.imgur.com/abDpq.png[/IMG]

---

### Post by mörgæs on 2019-12-07
Please post the output from ```
hciconfig -a
``` in CODE tags.

---

### Post by amith3 on 2019-12-08
I made it working somehow. Not sure how. I think the problem was with  pairing. I disconnected (unpaired) all other devices including my  android phone. Then tried again. It got connected in the first attempt  but audio was not coming. After trying multiple times connecting and  disconnecting the device using bluetooth manager and powering ON and OFF  the headset, It's working well now. But I'm afraid if it'll get connect  after I reboot my system. I don't have a systematic plan to get it  working. It was just trial and error!!

---

