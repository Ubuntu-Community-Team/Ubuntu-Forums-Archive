---
title: "Very slow wireless... what gives?"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by AMD RULES on 2011-06-30
I have this card in my desktop.  

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320048&cm_re=Asus_n-_-33-320-048-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320048&cm_re=Asus_n-_-33-320-048-_-Product)

The signal in the same room isn't as good as my laptop and the internet is a lot slower too.

Do I need to change a setting or something?  I'm new to linux so any help would be greatly appreciated.

Thanks!

---

### Post by dFlyer on 2011-06-30
I had a bad antenna on my desktop wifi card that was causing a poor connecting speed.

---

### Post by chili555 on 2011-06-30
> **AMD RULES said:**
> I have this card in my desktop.  

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320048&cm_re=Asus_n-_-33-320-048-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320048&cm_re=Asus_n-_-33-320-048-_-Product)

The signal in the same room isn't as good as my laptop and the internet is a lot slower too.

Do I need to change a setting or something?  I'm new to linux so any help would be greatly appreciated.

Thanks!Let's take a look. Please open a terminal and run and post:```
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

