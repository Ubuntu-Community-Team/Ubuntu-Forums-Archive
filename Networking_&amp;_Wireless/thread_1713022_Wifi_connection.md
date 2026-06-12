---
title: "Wifi connection"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by captzu777 on 2011-03-23
My wireless adapter is working and tell me i am connected but when I open the Firefox browser ,tell me that can not find the server,can somebody help?
thanks

---

### Post by SecretLegend on 2011-03-23
run:
```
sudo ifconfig 
```


Then paste the output also what wireless card is it?
To find that out:

```
sudo aptitude install wireless-tools
```

then:
```
iwconfig

```

And post the output of that :D


Btw all these commands are ran from terminal <--- thought I should make that clear before you didn't know what I was talking about...

---

