---
title: "Can't find cracking package"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by andru183 on 2010-02-09
I'm trying out something I came across in EPA cracking in this guide
[http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks](http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks)
but it asks you to install packages I can't find and I'm wondering if anyone can help
I installed I think it was airodump -ng but it's not enough to complete the guide, I understand some packages come with airodump but I don't know where to get the rest, thanks
and this is purely to test the strenght of my router, I'll be moving into an aperment block soon and could do without smochers smoching my internets!

---

### Post by chili555 on 2010-02-09
Did you install aircrack-ng? You can do so in System -> Administration -> Synaptic. Then do:```
man aircrack-ng
man airodump-ng
```> this is purely to test the strenght of my router,Right.

---

### Post by cariboo on 2010-02-09
You really don't need to go through all that, just use a good strong wpa password, you can go [here]("https://www.grc.com/passwords.htm") to have one generated for you. This will make your wireless setup about as secure as it can get.

---

### Post by andru183 on 2010-02-09
Yep chilli555 I've em installed but when I go to use the first ./airodump command it says no such file exists so I figure a not fully installed package, no?

---

### Post by chili555 on 2010-02-09
Hmmm. You just said you installed airodump-[COLOR="Red"]ng[/COLOR]. If you installed it from the Ubuntu repositories then you don't need [COLOR="Red"]./[/COLOR]. Please try:```
sudo airodump-ng wlan0
```Substitute your wireless interface, if it's not wlan0.

---

