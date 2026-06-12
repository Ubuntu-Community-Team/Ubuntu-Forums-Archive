---
title: "Ubuntu 10.04+thinkpad x200t+nokia 5230 as modem=freezing..."
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by vickoxy on 2010-12-19
Hi,
i followed instructions here to use my nokia 5230 as modem:
[http://wiki.ubuntuusers.de/UMTS_per_Mobiltelefon](http://wiki.ubuntuusers.de/UMTS_per_Mobiltelefon)

It works fine. But, as soon as i turn off the line or close the browser, computer freezes - black screen with few terminal lines same as those when i start or logout the computer. And nothing, i have to push start button to restart it. Any idea?

---

### Post by vickoxy on 2010-12-20
No one?

---

### Post by vickoxy on 2010-12-21
This only happens if i use cell phone as USB Modem. With Bluetooth connection it work s just fine.

---

### Post by gloawu on 2010-12-22
Are you using Chromium as your browser? If yes, then other people are having the same issue ( [http://www.google.com/support/forum/p/Chrome/thread?tid=6b76aaff509c77cf&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=6b76aaff509c77cf&hl=en) ). Im using my netbook an my nokia 5230 via a usb-cable for mobile broadband. Apart from this issue: how did you get it working with bluetooth? It doesnt show up in network manager when im using bluetoothe...

greetings

---

### Post by vickoxy on 2010-12-23
I think it has nothing to do with chrome browser-if i minimize or close any app window it freezes. 
I used instructions here:
[http://wiki.ubuntuusers.de/UMTS_per_Mobiltelefon](http://wiki.ubuntuusers.de/UMTS_per_Mobiltelefon)

So, if you want to setup your cell phone as modem, all is going automatically:

1) connect your cell phone with usb with computer
2) on cell phone choose pc-suite or similar...
3)run in terminal sudo ```
wvdialconf
``` 
 
If you want to have bluetooth connection;

4) edit $ sudo gedit ```
/etc/wvdial.conf
```
5) for **modem** type **/dev/rfcomm0**
6) delete line with ```
Modem Type
```

7) open terminal and establish bt connection with ```
sudo rfcomm connect 0
```
8) open another terminal (do not close step 7 terminal) and type ```
sudo wvdial
```

For step 7 and 8 i made one little script and put it on panel to make all automatically:

```
#! /bin/bash

sudo /usr/bin/rfcomm bind **0 C5:96:9V:75:3C:9D 22**
sudo wvdial
```

(you have to give your isdn number, cell mac and channel...)

I am using now bluetooth connection because it is quite fast-much faster than under MacOS...

---

### Post by gloawu on 2010-12-23
OK, I somehow managed to get everything working just like i wanted it to be in the first place.

Problems: in order to get mobile broadband working with my netbook and my nokia 5230 phone i had to connect the devices with a usb-cable, because network-manager didnt show up an option to connect to mobile broadband whenever i connected the devices via bluetooth. Also, whenever i used chromium for browsing or disconnected the cable, the computer froze when exiting chromium browser (yes, completely, i had to turn it off an on again. For more information on this problem see the link in my previous post...).

Solutions: after some time spent fiddling around i tried the blueman bluetooth manager and told it to connect to the dialup service via a right-click on the device. Well, then it just worked, network-manager showed up the option to connect to my mobile broadband service. The only thing i have to do after each restart is right-clicking the device in blueman an tell it to connect to the dialup service and confirm the connection-request on the phone. In addition, i disabled the standard ubuntu program for managing bluetooth devices via gnome menu-system-preferences-startup applications because blueman seems to be a far more sophisticated program that the one shipped with ubuntu at the moment. The problem with the system freeze when using chromium browser also just went away by using bluetooth instead of the usb cable.

Now im just happy i got things working just right and without having to do very much tech stuff. 

Please let me know if this solution (or workaround?) works out for you too.

Regards and "frohe Weihnachten" :)

---

### Post by vickoxy on 2010-12-23
Hi,
i can not test now any usb-connection, but i am very happy with bluetooth connection-see no difference in speed.

I don´t use network-manager or blueman to establish my bt connection-i make it all from terminal, and it works really perfect. No restarts or something like that. 

So, if i understand you-no problems with bt? Same with me... USB Modem causes freezing under chrome? Same with me, but as said-i am happy for now with bluetooth connection...

Thanks and "frohe Weihnachten":popcorn:

---

