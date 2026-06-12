---
title: "my wlan0 dissapeared!!"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by Awareness on 2009-01-25
my wlan0 disappeared....instead a eth1 appeared... and the thing is... its connected and working...

im clueless what just happened... since this is a new laptop and I've been messing around for 2 days without problems and I barely installed anything aside from compiz... I just rebooted the laptop and the change was there...

Im completely clueless... any thing i can check? any guess? :)

---

### Post by Sam Lars on 2009-01-25
As a general rule, unless you're looking for trouble, if it works, don't mess with it.
Some drivers use different names for the device.  Your driver may or may not have changed, I don't know.

---

### Post by Awareness on 2009-01-25
well, the connection icon disappeared on the sysbar...

I need that icon, because this laptop is not mine... Its for my mom, and she will need it to scan networks... She doesn't really understand much about computers

---

### Post by Sam Lars on 2009-01-25
If you mean the Network Manager, you can start what with
```
nm-applet
```
If you mean the little Gnome Network Monitor, you can change the settings as to what device it monitors.

---

### Post by Awareness on 2009-01-25
thanks for quick response :)

how?

---

### Post by Sam Lars on 2009-01-25
Which one?
You can run nm-applet in Alt+F3, on a terminal if you want to.
If you right click on the Gnome applet and go to the properties, you can change what it's monitoring.

---

### Post by Awareness on 2009-01-29
Thanks Sam!!!

I found the answer in this thread
[http://ubuntuforums.org/archive/index.php/t-527735.html](http://ubuntuforums.org/archive/index.php/t-527735.html)

I guess the interface was eth1 all this time... Its just ive messed with several laptops and its always been wlan0 :)

The problem was i somehow deleted the notification area in the panel :)

I added it again, and everything is back to normal ;)

Thanks again

---

