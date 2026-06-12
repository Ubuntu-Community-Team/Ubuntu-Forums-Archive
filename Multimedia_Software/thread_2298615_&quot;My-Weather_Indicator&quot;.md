---
title: "&quot;My-Weather Indicator&quot;"
date: 2015-10-12
forum: Multimedia Software
---

### Post by ray9 on 2015-10-12
Is "My-Weather Indicator" down or is just mine?  I reinstalled it but I forgot the launch command.   Information appreciated.  I've read to look in the "start-up" menu but I don't have that, when I click the power button I get  "system settings"  not "start-up".  Ubuntu 14.04LTS.

---

### Post by shantiq on 2015-10-13
hi Ray does it start if you run :

```
/opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator
```    in your terminal?

then maybe to place it


as autostart [so you do not have to think about it]

copy and save following in a text document like Gedit in  **~/.config/autostart**


```
[Desktop Entry]
Type=Application
Exec=/opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=my-weather-indicator-autostart
Comment=My-Weather-Indicator official shortcut
X-GNOME-Autostart-Delay=2


```

---

### Post by ray9 on 2015-10-14
Thank you for the reply.  I entered  the information given and the terminal said it was running.  But it's not.  ??  On edit I got it running.  Thanks.

---

### Post by ray9 on 2015-11-02
It started working.

---

