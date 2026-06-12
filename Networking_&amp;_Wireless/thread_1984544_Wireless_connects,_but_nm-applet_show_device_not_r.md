---
title: "Wireless connects, but nm-applet show device not ready"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by dcroxton on 2012-05-21
My networking works, which is good.  But the nm-applet doesn't reflect this; it shows my wireless as "device not ready."  Therefore, when the connection goes down, my only recourse is to restart networking & network-manager to force a reconnect.  (Well, probably there is some command line command I could use, but I don't know it and would rather not get into it.)

I found something about devices being set to unmanaged by default in /var/lib/NetworkManager/NetworkManager.state, but I changed WWANEnabled=true and restarted every networking service I could think of, but I still don't get anything out of nm-applet.

Can anyone help?

Derek

---

### Post by dcroxton on 2012-05-22
Never mind, the next reboot fixed the problem (I'm assuming it was changing NetworkManager.state that was the key).

I wish Ubuntu wouldn't change settings like that on upgrade without some kind of notification.  I mean, if there is a good reason for, okay, but please include some popup to the effect:  "Note: your networks will be unmanaged until you change this setting, go to [http://whatever](http://whatever) for an explanation."

---

### Post by dcroxton on 2012-05-24
Bother, now it is doing it again!  As I type this, the nm-applet icon tells me that I am not connected and shows no networks to connect to...and yet I am on the internet.  If I lose the connection, I will have to restart networking + probably network-manager.  Any idea why this is happening -- and how to fix it??

---

