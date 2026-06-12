---
title: "Realtek RTL8187 ( device not managed)"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by PROFE$$OR on 2010-04-27
hi guys
     I have a problem with my internet connection this is the picture the device is Realtek RTL8187.[[IMG]http://uploadpic.org/thumb-56684.jpg[/IMG]](http://uploadpic.org/showpic-56684/wireless.html)
i didn't know how can i manage this device to work so could you help me i don't have an internet connection in ubuntu right know and i really wanna move to ubntu my verison is 9.10  :confused::confused:

---

### Post by PROFE$$OR on 2010-04-27
UP UP UP
guys please help meeeeeeeeee

---

### Post by PROFE$$OR on 2010-04-27
Hi guys please help me
 
two weeks and i didn't fix this problems :confused::confused::confused::confused::confused:

---

### Post by PROFE$$OR on 2010-04-27
what is the problem in this site 24 viewor and no one reply and in the url above more than 40 viewor and no one reply that is so bad

---

### Post by PROFE$$OR on 2010-04-27
that is so so bad more than 40 viewor and no one reply ohhhhhhhhhhhh shut

---

### Post by Iowan on 2010-04-27
Threads merged.
From Code of Conduct: > Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.
...
Please do not cross post, or post the same thing in multiple locations.
Once/day is generally considered adequate for thread "bumping".

Now - on to the problem...
From a terminal: (Applications>Accessories>Terminal): ```
cat /etc/network/interfaces
``` Does the file have more than these two lines:```
auto lo
iface lo inet loopback

```

---

### Post by conradin on 2010-04-27
Here is a similar thread for wired networks:
[http://ubuntuforums.org/showthread.php?t=1109585](http://ubuntuforums.org/showthread.php?t=1109585)

---

### Post by PROFE$$OR on 2010-04-27
thank you for your help this is the out put
:
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider
auto wlan0
iface wlan0 inet manual

---

### Post by PROFE$$OR on 2010-04-27
> Here is a similar thread for wired networks:
[[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=1109585[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1109585")
i'm sory i'm new on ubuntu how can i make manage=flase to manage=true could you give me the command

---

### Post by Iowan on 2010-04-27
Depending on whether you prefer **nano** or **gedit** as an editor:```
sudo nano /etc/NetworkManager/nm-system-settings.conf
```or```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by PROFE$$OR on 2010-04-28
thank you guys so much thats really worked

---

### Post by cbbnewbie on 2010-05-03
hi i have this usb wireless lan realtek RTL8187 and i dont know how it works in ubuntu 10.04 im a total new ubuntu user. im using windows xp atm because i cant connect to the internet when im in ubuntu please help thanks

---

