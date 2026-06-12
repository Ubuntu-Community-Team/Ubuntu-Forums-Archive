---
title: "how do I make the wifi icon to appear on taskbar?"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by madhavhmk on 2009-08-20
Thanks to some of the brilliant, meticulous tutorials provided in the forums, I was able to resurrect my wifi access on linux yesterday....

I just need one more final touch to it, to  make the wifi icon(the one showing signal strength).... i ll be glad if someone could help me here....!!!



Thanks

---

### Post by warreno on 2009-08-20
Right-click the top bar, select "Add to panel…" and choose "Notification Area". That's what contains that sort of information on my netbook, anyway.

Hope this helps.

---

### Post by madhavhmk on 2009-08-20
Thanks for the reply.....
I tried that, but it doesnt have the wireless icon on it....it has blutooth, charger and LAN settings.......

---

### Post by t0mppa on 2009-08-20
In that case you probably closed the network manager applet and to get that back up and running, press Alt + F2 and type in **nm-applet** and click run.

---

### Post by warreno on 2009-08-20
Hmm. [This thread]("http://ubuntuforums.org/showthread.php?t=960966") might be worth a look; it links out to [here]("http://ubuntuforums.org/archive/index.php/t-109524.html").

---

### Post by madhavhmk on 2009-08-20
I tried them, and also the thread points to the fact that the applet is a part of notification area....

I have the notification area but, in it the only icon related to network is the icon"manual network configuration"......

---

### Post by warreno on 2009-08-20
Wow, okay, you know what? This is just stupid. Nothing seems to work for me either.

I mean nothing.

An hour Googling and poking and prodding and trying, and *nothing*. nm-applet doesn't seem to want to present a GUI, and I can't see anything in the login or session options that makes a difference.

This is just baffling and stupid. Where the heck are the wireless LAN bars in the Ubuntu 9.04 GNOME panels?

---

### Post by neophyte_7 on 2009-08-21
Be cool Madhavhmk ............I think you are missing out the obvious....the wireless indicator is actually the icon called 'network monitor' that is inside the list of 'add to panel'

if your nm-applet is up and running and wifi is ok, the icon ought to display the signal strength....although not in flashy lines, but % strength as bar graph....

---

### Post by madhavhmk on 2009-08-21
Thanks a lot neophyte_7..!!!

the icon was indeed the network monitor and not the one inside notification area.......


problem solved here....!!:guitar::lolflag::popcorn::KS:)

---

