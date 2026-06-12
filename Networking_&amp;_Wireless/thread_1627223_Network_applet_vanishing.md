---
title: "Network applet vanishing"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by motiur on 2010-11-21
Hi , I am using Ubuntu 10.04 LTS . I encountered a serious nagging problem recently . I have my wireless driver installed just a couple of days back . The network-manager applet situated beside the time and date applet showed that I was receiving wifi signals correctly . I was using broadband connection and I was not subscribed to wi-fi services. My university has free wifi service and I was happy to subscribe to it.

Unfortunately the applet responsible for showing network connections disappeared . I could not bring it back despite applying (FN + F3 , this enabled the wifi signal correctly as displayed in the red signal of the laptop) , however lack of the applet prevented my ability to connect to the university wifi system . Under System->Preference menu the Network Connection was present though , but did not show wifi signal . My broadband connection nonetheless is working fine . 

Long story short , is there a way to bring back the applet for network-manager which is present by default beside the date and time applet .

---

### Post by dineshs on 2010-11-21
Rightclick on panel-add to panel-select [COLOR="Blue"]Notification area[/COLOR] then add.
If it doesnt work ,run
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```and set```
managed=true
```
Restart machine

---

