---
title: "Ubuntu and 3g wireless modem dongles"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by jonndoe45 on 2011-10-06
I live and work in Cambodia, here the internet is seriously expensive and the ISP's does as much as possible to discourage you to use their service. 

It seems the ISP service plan I use (unlimited use, $88 pm, top speed 4mb), has been meddled with in recent weeks.    

What they seem to be doing is disconnecting the user after x hours, approximately 4 hours or so, it seems (not yet verified by the staff in the mobile/ISP shop, but heck I doubt the bosses would bother to tell the underlings their policy decisions).    

In Ubuntu, to reconnect you just click on the mfone connection once you've enabled mobile broadband, but unfortunately just reconnecting doesn't work, what you have to do it seems is disable mobile broadband, re-enable it then connect to mfone.    

Now for any linux / ubuntu guru's the network manager can retry auto connect but this just doesn't work, anyone know how to automatically disable/enable mobile broadband, then reconnect, if a mobile broadband connection is disconnected ?    

Many Thanks

---

### Post by alexfish on 2011-10-07
a provider sometimes disconnect the cell if not in constant use, this is done to save your data usage or to allow others to access the network, 

unless the modem manager recognises there is a disconnection then it is impossible to reconnect , try from the terminal ```
sudo killall modem-manager
```see what happens

can also suggest trying sakis3g,

regards

alexfish

---

