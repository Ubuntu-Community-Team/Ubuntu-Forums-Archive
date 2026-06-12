---
title: "Sound Card Not Found on Sony Vaio VPCEB15FM"
date: 2010-06-09
forum: Multimedia Software
---

### Post by webmehedi on 2010-06-09
Hello. I am a windows user. Recently i installed Ubuntu 10 version on my laptop **Sony Vaio VPCEB15FM**. Specification link :
[http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?storeId=10151&catalogId=10551&langId=-1&productId=8198552921666125435](http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?storeId=10151&catalogId=10551&langId=-1&productId=8198552921666125435)

And after installing , i was really happy on Ubuntu. Its really looking good. But i am unhappy on Sound Card. I think my sound card driver was not found. I did some updates [Ubuntu software updates], but still soundless. 

I want to use ubuntu. but without soundcard its really impossible to use.

So if any one know the solutions please help me to find the solutions of my sound card.

Please tell in details, bcz i am a new user of ubuntu.

Waiting for reply.


Thanks

---

### Post by lidex on 2010-06-09
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by webmehedi on 2010-06-10
hello lidex. thanks for reply. here is the output ...


uname -a
========================================================
Linux ubuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux


aplay -l
========================================================
aplay: device_list:223: no soundcards found...



cat /proc/asound/version
========================================================
cat: /proc/asound/version: No such file or directory



head -n 1 /proc/asound/card*/codec#
========================================================
head: l: invalid number of lines


thanks

please let me know what i will do now .

---

### Post by lidex on 2010-06-11
Looks like your alsa install is borked. Try using the alsa-upgrade link in my sig to fix it.

---

### Post by webmehedi on 2010-06-12
thanks a lot lidex. now i can hear SOUND. thanks a lot again.:popcorn:

---

### Post by lidex on 2010-06-12
Alright, some good news today! Please mark the thread as solved using 'Thread Tools' up top.

---

