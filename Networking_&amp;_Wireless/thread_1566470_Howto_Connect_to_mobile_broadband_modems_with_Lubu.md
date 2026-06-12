---
title: "Howto: Connect to mobile broadband modems with Lubuntu"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by AndyM3 on 2010-09-02
I had this problem and I saw others have it too. So I decided to post what worked for me. YMMV, of course.

The solution is dead simple: just install the "modemmanager" package, plug in your modem and reboot. Then, just click the network icon in the tray, select your modem and configure it.

Note that you can also do this if you don't have an Internet connection. Download Keryx from [here]("http://keryxproject.org/") and use the tutorial [here]("http://keryxproject.org/tutorial/").
The tutorial is a bit unclear, so let me specify: create the project on your **offline** machine, open it on your **online** machine, let it download the new package lists, download all updates (there is a button for this), search for and download modemmanager and install the packages on your **offline** machine. Clear now? :D

Feel free to correct, contradict and flame me :mrgreen:

---

### Post by phillw on 2010-09-26
Courtesy of one the guys on the IRC channel, you can also try this  method [3G Workaround](http://forum.phillw.net/viewtopic.php?f=18&t=92)

Regards,

Phill.

---

### Post by AndyM3 on 2010-09-26
> **phillw said:**
> Courtesy of one the guys on the IRC channel, you can also try this  method [3G Workaround](http://forum.phillw.net/viewtopic.php?f=18&t=92)

Regards,

Phill.

I was aware of that method, but I don't think Ubuntu newbies (including me) will find it easy. Also, it requires a phone number if I understand correctly, so it doesn't work for me (my carrier uses just APN; no phone number, no username, no password).

---

