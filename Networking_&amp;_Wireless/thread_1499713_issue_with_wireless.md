---
title: "issue with wireless"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by levis lover on 2010-06-02
hello guys, i am having trouble with my wireless internet.

My ISP provided the modem from Nokia/Seimens Technology, **IP** address, **Subnet** Mask and **Default Gateway**.
When i started Ubuntu saved all this information into the wireless properties.

_But the problem is that i need a dialer which can dial the Username/Password and can autheticate me._

---

### Post by levis lover on 2010-06-02
didn't knew it was so simple ?

there are only two commands you need to run to get wireless working..

select the wireless network..
then
```

sudo pon dsl-provider
```

then 
```
sudo pppoeconf
```

It will start a blue screen which will ask a few questions and permissions and then will ask the username and the password that has been provided by the ISP.

---

