---
title: "&quot;Device not managed&quot;"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by FrontalNoize on 2009-10-18
Hi,

I'm experiencing a little error for my internet connection on Jaunty Jackalope.  
When I click the network manager, it states for both the wired and the wireless connection "device not managed"

For the wired connection, this seems to be not much of a problem.  I can connect to the Internet without troubles, though I cannot find the connection in the Network manager (in fact, it has the two screens with a red x in the right-bottom corner, indicating that technically I have no Internet).  
For the wireless, there is a problem.  That one doesn't configure automatically, I suppose.  We have a secure wireless at home.  Probably he would find a non-secured network, I do not know.  

Might this have to do with the drivers?

---

### Post by FrontalNoize on 2009-10-18
I unplugged the cableconnection, plugged it back in while still logged on and tried to reconnect.  Which failed.  Tried to log off and back on, still didn't work.  All this with GNOME.  

I then tried to log in on a KDE-session.  Now my connection works again.  Haven't been able to log out yet (downloading some packages) and relogin on GNOME to check if I have internet there aswell.  

Weird stuff.  The window managing system shouldn't have anything to do with my internet, should it?  Unless swapping from GNOME to KDE triggered the system to check the cable connection again, in which case it should be fixed on GNOME aswell next time I login...?

Anyways, the whole issue seems to be that I can't get automatically connected due to that "device not managed" thingie.

---

### Post by quack on 2009-10-18
I had a similar problem today.

For ME it turned out to be because I'd upgraded to Jaunty from a previous version. The previous version (or maybe something else I'd fiddled with) had put information about my network interfaces into /etc/network/interfaces and the GNOME Network Manager sees that and says "whoa - someone else is handling those interfaces so I'll steer clear of them"

Your problem may be different but if I were you I'd check in /etc/network/interfaces and comment out anything you find in there. The Network Manager then needs a restart - in fact safest bet is to reboot the machine.

(With help from: [http://www.craigmayhew.com/blog/2009/06/ubuntu-904-wired-network-device-not-managed/](http://www.craigmayhew.com/blog/2009/06/ubuntu-904-wired-network-device-not-managed/))

---

### Post by lswb on 2009-10-18
Very likely what quack said is the problem, however, the loopback interface should not be commented out of /etc/network/interfaces. i.e. do not delete or comment out these lines:

```

auto lo
iface lo inet loopback

```

---

