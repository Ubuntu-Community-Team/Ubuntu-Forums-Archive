---
title: "ubuntu wont connect to secure wpa2"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by Alex715 on 2011-07-05
Hi after recently installing ubuntu 10.10 which didnt work wpa2 then upgrading to 11.04    my laptop wobt connect to a wpa2 or maybe other types of secure wifi but will conect to open networks. wpa2 has always worked with my windows xp install so to be honest i dont know what to do any help would realy be appreciated. thanks in advance

---

### Post by poolet on 2011-07-05
hello,

try to use wicd instead of network manager..... If isn't fix your problem,
login to your modem/router with windows and change the encryption to WEP but use own  password....

---

### Post by SteveDee on 2011-07-06
If you can live with the weak protection of WEP then this may be your easiest option.

My understanding is that wpasupplicant deals with wpa encryption but there may be limitations with your network driver. So I suggest you do some searching using your driver name, "wpa" & "wpasupplicant" and see if there are any known issues (& possible fixes).

---

