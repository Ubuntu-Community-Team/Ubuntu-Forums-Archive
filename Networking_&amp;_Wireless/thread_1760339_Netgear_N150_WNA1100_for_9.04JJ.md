---
title: "Netgear N150 WNA1100 for 9.04JJ"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by Deciple X2 on 2011-05-16
hey everyone I need help trying to get a netgear N150 WNA1100 wireless adaptor to work with ubuntu 9.04. My problem is, is that when I plug in the adaptor to any of the usb ports it doesn't power up however when I check to see if it comes up in the terminal it does. Also I don't think I have to state this but it because of this it detect any wifi. 

I've looked around on a bunch of different forums and tried a bunch of different things, but none of solutions were geared towards the version of ubuntu that I am using. 

If you can help me out please be give detailed information because I am new to linux and I'm still learning how to handle ubuntu.

Thanks

---

### Post by Deciple X2 on 2011-05-18
any one got any ideas?

---

### Post by walt.smith1960 on 2011-05-18
I haven't tried on 9.04 but this works on 10.04 and 10.10.  Netgear's WNA1100 is an ath_9k based device.  I used this from sourceforge:  [http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/). There are 2 entries.  The original installer worked in 10.04 but not in 10.10.  The later release fixed that.

 Using this is a 2 stage process.  First you install the .deb using whatever procedure you prefer.  This will install an entry under Applications -> System Tools. Running that installer from an account with SUDO privileges-it takes a few minutes and will look like it's hung- then rebooting should bring your WNA1100 to life.  If you choose to upgrade to a current Ubuntu release(11.04/2.6.38),  your WNA1100 should work without any tweaking; mine did.  

You do know that support for Jaunty ended on 10 Oct. 2010, right? No security or other updates?

---

### Post by Deciple X2 on 2011-05-19
thanks for the help but that didn't work, I guess I'll just upgrade to 11

---

### Post by walt.smith1960 on 2011-05-20
> **Deciple X2 said:**
> thanks for the help but that didn't work, I guess I'll just upgrade to 11
You might want to try a live CD/USB install of 11.04.  There are aspects of it that are .......controversial.  I don't know if Unity will work on a live session or not.  Unity depends on hardware graphics acceleration so depends on whether there's a proprietary driver need for your graphics card.  10.04 and 10.10 are both actively supported (10.04 longer because it has  LTS)and I've gotten my WNA1100 to work on both with the .deb file. If you're happy with 11.04 in "classic" mode which is quite similar 10.10 then cool.  Classic mode will run without  proprietary drivers.

---

### Post by Deciple X2 on 2011-05-27
sorry for the long delay, been away from the machine for a while. Before I update I just thought about something, is my machine is up there in age so I'll have to check if I can even do 11. I'm running Pentenium 4 2.53 GHZ on 495 mb of ram...

---

