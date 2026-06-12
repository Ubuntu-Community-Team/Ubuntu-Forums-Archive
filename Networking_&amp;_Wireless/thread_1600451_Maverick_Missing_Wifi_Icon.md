---
title: "Maverick: Missing Wifi Icon"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by klausner on 2010-10-19
I was messing around with the toolbars on a new installo of maverick 10.10, and now I have no wireless icon. How can I replace it, its not in the *Add to Panel* menu.

Also, I noted before I lost it that the wifi icon had no *move* or *lock to panel* options.

---

### Post by dineshs on 2010-10-19
You mean Network manager icon?
)Right click on the top panel-click add to panel-select notification area -click add
If it doesnt work please post the result of
```
sudo gedit /etc/network/interfaces
```

---

### Post by klausner on 2010-10-19
> **dineshs said:**
> You mean Network manager icon?
)Right click on the top panel-click add to panel-select notification area -click add
If it doesnt work please post the result of
```
sudo gedit /etc/network/interfaces
```

As I said in the original post, there is nothing in the *add to panel* menu you get by right clicking. The interface exists, and the wifi connects on previously set parameters.

---

### Post by trellis2 on 2010-11-13
Rt click in panel
"Add to Panel"
scroll down to "Notification Area" and click.
Now I have bluetooth, ubuntucloud, battery and, wifi icons back. 
Thank you Dineshs!!!

---

