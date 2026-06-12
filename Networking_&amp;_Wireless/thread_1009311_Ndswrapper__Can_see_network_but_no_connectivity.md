---
title: "Ndswrapper:  Can see network but no connectivity"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by kingkorn on 2008-12-12
Hello,

I just intstalled 8.10 on my laptop.  Everything works but the wireless.  I found a linux driver for my wireless card, but could not get the system to recognize it even though the system sees my wireless card.  The card is: Realtek RTL8187se wireless LAN controller.  

I found an interface that allowed me to use NDSWRAPPER and chose the windows driver and it setup a wireless connection.  I can see the network now, but cannot use it. 

When I clicked on the 'configure network' button, NDSWRAPPER gave this error: no network manager program found, or something equivelant.  

I then installed gnome-network-admin, which seemingly went off without a hitch.  Now when I click on configure network, the gnome network admin applet comes up, but everything is grayed out.  I have a feeling that it is locked.  I must be opening it without admin permissions.  I am a command line retard so I dont know how to start the applet from command line.

The laptop I am using had Vista on it and I was stuck using it because I needed it for several programming classes at college.  Now that the quarter has ended, and being thoroughly fed up with crappy windows products, I am hell bent on getting this to work properly.  

Please someone help me?

Thanks

K.K.  :confused:

---

### Post by albinootje on 2008-12-12
As an alternative you can also install wicd : [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by kingkorn on 2008-12-12
How would I start gnome network admin applet from command line with admin rights (unlocked)??

---

### Post by albinootje on 2008-12-12
Is your user in the admin group ? 
If your user isn't, then that explains the greyed out area.

---

### Post by kingkorn on 2008-12-13
> **albinootje said:**
> Is your user in the admin group ? 
If your user isn't, then that explains the greyed out area.

Yes, my user is in the admin group.  I still wish to know how to start the applet from command line.  Anyone?

---

### Post by Howinlinux on 2008-12-13
gksu or sudo  
**Vulnerable in this termporary state**

---

