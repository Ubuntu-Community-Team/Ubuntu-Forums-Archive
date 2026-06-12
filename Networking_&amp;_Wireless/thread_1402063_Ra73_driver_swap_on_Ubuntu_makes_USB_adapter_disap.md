---
title: "Ra73 driver swap on Ubuntu makes USB adapter disappear . How do I bring it back?"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by 9Shenandoah on 2010-02-08
[FONT=Times New Roman][SIZE=3]I am using Ubuntu Incredible Ibex on a Lenovo T400 with a Hawking HWUG1 USB adapter. I was successfully capturing WPA handshakes good enough for Aircrack-ng. However they didn’t satisfy Cowpatty. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]The built-in wireless adapter on my Lenovo T400 appeared as wlan0. The [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]HWUG1 USB[/SIZE][/FONT][FONT=Times New Roman][SIZE=3] adapter appeared as wlan1. The “airmon-ng start wlan1” command configured the HWUG USB adapter as mon0.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Things were okay but not great. I wanted to use Cowpatty and the Rainbow tables but my captures weren’t satisfactory, except for the ones on my own router five feet away. I even tried using a 3 foot omni 12 dB antenna[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I started to suspect my drivers.I was using the drivers that came with Ubuntu Incredible Ibex.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I saw the website [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]http://www.aircrack-ng.org/doku.php?id=rt73[/SIZE][/FONT]]("http://www.aircrack-ng.org/doku.php?id=rt73")[SIZE=3][FONT=Times New Roman] and followed the instructions carefully to install the **rt73-k2wrlz-3.0.3 **driver.[/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]When I ran “Airmon-ng start wlan1”, I saw that the Hawking was indeed now rausb0 and using the rt73 driver.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]When I ran “Aireplay” on my WIFI router to de authenticate myself I got 0/0 acks. Previously I was getting something like (63/66 acks).It also happened on other test routers.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]So I did some more reading and I was thinking the rt73-k2wrlz-3.0.3.driver was incompatible with the Incredible Ibex kernel and Ubuntu. I found the site [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]http://mcmlxxii.co.uk/2008/10/22/rt73-ubuntu-intrepid-8-10/[/SIZE][/FONT]]("http://mcmlxxii.co.uk/2008/10/22/rt73-ubuntu-intrepid-8-10/")[FONT=Times New Roman][SIZE=3] and followed the instructions to install the **rt73-cvs-daily **driver. However I didn’t install WICD.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]After that, my HWUG1 USB disappeared completely as well as wlan1. It doesn’t show up when I run the “ifconfig” command. However my built-in onboard wireless adapter shows up as wlan0.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]How can I bring back the wlan1 and my Hawking HWUG1 USB adapter? Furthermore how can I reinstate the original driver that I was using?[/SIZE][/FONT]

---

### Post by 9Shenandoah on 2010-02-09
Do you think my USB adapter is dying? The new driver displayed quite a few AP's under Airodump but perhaps its Tx function is lost.

---

### Post by 9Shenandoah on 2010-02-09
Thats a possibilty, but you said that it worked when you used your Thumb Drive and under Linux.

---

### Post by 9Shenandoah on 2010-02-09
True, but I didn't do a detailed analysis. I see its green light flashing all the time under Windows but never under Linux.
 
Have you checked the USB port? I know you have a Lenovo but even they make faulty equipment.

---

### Post by 9Shenandoah on 2010-02-09
Darn you see a few threads where 20 experts hop in and solve the problem and you see some threads where no one answers.
 
Anyway after Manning brought the Colts ahead 13-10, I thought they had the game won. Football is much more than strategy. The Saints had the underdog factor.

---

### Post by 9Shenandoah on 2010-02-09
Reinstalling seems like a viable solution.
 
The Colts are still a better team than the Saints. The Saints did the same thing that the Giants did the year they won. A mediocre team got some lucky breaks. Got to hand it to them, they played hungry.

---

