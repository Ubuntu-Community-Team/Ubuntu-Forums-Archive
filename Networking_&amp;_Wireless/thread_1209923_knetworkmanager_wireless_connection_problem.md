---
title: "knetworkmanager wireless connection problem"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by guedesav on 2009-07-10
So, suddenly my wireless connection stopped working. For the record, I can still connect to the router by wire(just as I'm doing right now) or wirelessly from Windows Vista or even from a Nintendo DS, but in Ubuntu the only way I can connect to it is if the security is disabled(i.e., no security at all).

Here's something I think might be an important clue:

> 
 Setting '802-11-wireless-security' is not enabled, discarding
  Processing Setting '802-1x'
  Setting '802-1x' is empty, discarding


This is what knetworkmanager gives me when initializing, or if I change the password for the network connection. Either way, when I try to connect, it just displays

> 
Activate Connection /org/freedesktop/NetworkManagerSettings/Connection/1 on Device /org/freedesktop/Hal/devices/net_00_15_af_d5_dc_c7_0


and the icon on the tray doesn't even change, so I guess the connection isn't even starting at all.

The strangest part, though, is that I was connected to the router just yesterday night, and sudenly this morning it stopped working. The only change to the system I recall making was to install octave, so I have no idea whatsoever of what's going on.

Also for the record, I've found another thread about this same problem, but there was no visible solution. Someone told the guy to use wicd, but wicd just didn't work for me, so... any help, please?

---

### Post by grappler on 2009-07-10
I realise that I'm not really answering your question, but I am amazed that anyone has a working version of knetworkmanager. 

In the distribution I'm using (ubuntu jaunty kde 4.3 on a 64 bit machine) it was essentially impossible to configure when I installed in a couple of weeks ago - and there is a lot on the forums about this. I removed it and installed the gnome-network-manager applet which runs fine if you put it  (ie nm-applet) in kde autostart and which these days seems to work very well. It comes up in the system tray in the panel and is very configurable. 


In the past I've used wicd when nm-applet was not working well but it seems to me that nm-applet is currently working better than either of the other two.

---

### Post by guedesav on 2009-07-11
Well, I'm using fluxbox, and so using nm-applet is a bit hard, since it keeps complaining about some Dbus stuff... knetworkmanager, on the other hand, worked just fine with my Intrepid.

Now, I had hibernated my laptop before the error ocurred, and now I was forced to restart it, since hibernation went wrong(it stopped when it was returning to user space), and then... it was working again.

Thus, I guess it's some module or another that wasn't being loaded after hibernation...

---

### Post by guedesav on 2009-07-13
Okay, it happened again. I put the system to hibernate, when it came back, it gave me the same error as before. I see the pattern, but I just want to understand **why** leaving the wireless card connected while hibernating causes it to not work on the next wake-up. And it's not always, it's *just sometimes*, it hibernated 3 times before with no problem!

BTW, the card is a Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter

---

