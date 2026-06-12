---
title: "Force ubuntu to connect with wep"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by petrus250 on 2010-11-15
Hi everyone, I have been trying for weeks to connect to my wpa router. I have given up after many attempts and I would like to know if it is possible to make Ubuntu connect with wep even though network-manager recognises it as wpa-psk (I can connect with either to my router)

Thanks 

Peter

---

### Post by spiky001 on 2010-11-15
I connect to a router that has wpa and wep they have different names so i select the wep 1 enter the wep key all works, If I try the wep key on wpa it wont work, so can you set router to display both?

---

### Post by petrus250 on 2010-11-15
Hi, thanks for the reply...
The thing is, Ubuntu does not provide an option to use wep, only wpa-psk. The wep and the wpa-psk password are the same, maybe this where the problems stems from. Also, the router has no option to disable/change encryption if that is what you meant.

Thanks

---

### Post by spiky001 on 2010-11-15
I dont know much about routers just that the bt home hub at work allows me to connect either wpa or wep it lists bt home hub which is wpa or btfusion wep I can choose either from network manager, Now is it down to the router what is shown? maybe there is a setting in router you can change to wep?

---

### Post by cgb on 2010-11-15
You should be able to manually create the connection in Ubuntu.  You can go to the Application Menu/Preferences/Network Connections, then select the wireless tab..  Once here select Add and manually input your SSID and Wireless Security Settings.  This will allow you to specify WEP as the security type..

---

### Post by petrus250 on 2010-11-16
Thank you, I just tried that but no luck. I even tried to connect as if it was a hidden connection but Ubuntu still simply prompts me for the key over and over. Are there any other network managers?

---

### Post by cgb on 2010-11-16
There is other network managers available, wicd seems to correct some issues for people.  Have you ever been able to connect to this wireless router with any computer or device?  Also, have you ever been able to connect this Ubuntu PC with any other wireless router?

---

### Post by petrus250 on 2010-11-17
Hi, thanks for your help, I simply disabled wpa-psk on the router and it works fine now. I hope that ubuntu 11.04 will bring a fix but I guess I don't mind. Just a little bit less secure:)

---

