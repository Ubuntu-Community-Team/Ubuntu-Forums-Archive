---
title: "Wireless wont connect to secured network"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by Levakama on 2011-02-17
Hello, I have installed Ubuntu Maverick on my desktop PC yesterday.
I wanted to connect to my family secured network , it would keep connecting for a period of time ,then it would ask for PSK again and so on.
I use :Belkin f5d8053 N wireless usb adapter and the router is Belkin [F5D8233-4 N Wireless Router.]("http://en-us-support.belkin.com/app/answers/detail/a_id/521/session/L3RpbWUvMTI5Nzk1MTEwMi9zaWQvYW56d0dSbWs%3D")

I am not allowed to tinker with the security settings , but when I did turn off all security settings for a brief period of itime, it worked normally.
I cant therefore do any procedures on the Ubuntu installation that require internet connection.

The exact security settings are: 
Security mode :WPA/WPA2-Personal(PSK)
Authentication:WPA-PSK+WPA2-PSK
Encryption technique:TKIP+AES 


I use Windows 7 on the computer as well.

I would be happy if someone helped me resolve this issue.

---

### Post by Sean Moran on 2011-02-17
> **Levakama said:**
> 
I cant therefore do any procedures on the Ubuntu installation that require internet connection.

This is a side issue, but don't worry too much about Internet connections during the installation.  The install runs much faster and there's nothing you can't get later after the install is completed and you're running on the hard-disk.  I'm not at all familiar with secured networks, but I know a lot about installs.  Offline installs are fine, and quite a bit faster too.

---

### Post by wjz on 2011-02-17
Sounds like a driver issue. I have an atheros card and the native drivers were shocking at connecting to my wpa2 tkip router. And when it eventually did, speeds were slow. Same as you with security disabled things went as they should. Madwifi drivers fixed my problem. Heres the guide i used. [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html) .

 But bear in mind after an update it went back to the native drivers and i then had trouble installing madwifi again. So i used my custom ubuntu  version instead

---

### Post by Levakama on 2011-02-17
> **wjz said:**
> Sounds like a driver issue. I have an atheros card and the native drivers were shocking at connecting to my wpa2 tkip router. And when it eventually did, speeds were slow. Same as you with security disabled things went as they should. Madwifi drivers fixed my problem. Heres the guide i used. [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html) .

 But bear in mind after an update it went back to the native drivers and i then had trouble installing madwifi again. So i used my custom ubuntu  version instead
Can it be installed offline?

---

### Post by wjz on 2011-02-17
I reckon you will have to download the drivers and script so no. But it only takes 2 minutes so how about disabling security or connect with a cable.

---

### Post by Levakama on 2011-02-17
> **wjz said:**
> I reckon you will have to download the drivers and script so no. But it only takes 2 minutes so how about disabling security or connect with a cable.
I see.

---

### Post by Levakama on 2011-02-19
I am afraid that the procedure did not work, still no change.
Id also like to note that the PSK is a full sentence containing characters such as :Spaces, periods,á, exclamation mark.

---

### Post by grahammechanical on 2011-02-19
> Id also like to note that the PSK is a full sentence containing characters such as :Spaces, periods,á, exclamation mark.

That could indeed be the problem. My wireless key is 10 characters long. It is a mixture of numbers and letters. Someone is being too clever.

Regards.

---

### Post by Levakama on 2011-02-19
> **grahammechanical said:**
> That could indeed be the problem. My wireless key is 10 characters long. It is a mixture of numbers and letters. Someone is being too clever.

Regards.
What should I do then?
I cant change the password

---

### Post by Levakama on 2011-02-20
Any help?

---

### Post by Levakama on 2011-02-20
Bump.

---

