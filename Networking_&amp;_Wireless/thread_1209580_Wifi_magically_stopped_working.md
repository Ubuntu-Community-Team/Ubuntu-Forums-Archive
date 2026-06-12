---
title: "Wifi magically stopped working"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by rfsquared on 2009-07-10
Now I have to plug into ethernet.

The wireless was working perfectly fine last night and has been for the life of the ubuntu installation.  I put it on hibernate last night, went to sleep, woke up today and now my wifi will not connect.  Sometimes up at the top in the menu it says "Device Not Ready" but other times it doesn't really say anything.  I tried turning off and then back on my wireless card (you know, the little wifi button on the laptop), tried installing the madwifi drivers (it's an atheros card), then switching back to ath5k.

Don't know what else to do?

---

### Post by ajgreeny on 2009-07-10
Reboot? (Not hibernate!)  Or have you already done that?

---

### Post by clonne4crw on 2009-07-10
Yeah. Try a reboot. If your PC's anything like mine, when it first comes out of Suspend or Hibernate, it has a little trouble reconnecting to the network. If it doesn't reconnect in a few minutes, I reboot. Wifi sure is a magical thing...

---

### Post by rfsquared on 2009-07-10
I've rebooted 5 times.

Now here's something interesting I have figured out.

NOW, my wifi only works once I plug in the Ethernet cord to the laptop.  I get a little pop up notification under where the clock is (top right) that the ethernet is connected, then immediately afterward i get a notification saying my wifi is connected.

wtf?

---

### Post by ajgreeny on 2009-07-10
So are you saying the problem is nothing to do with hibernate, but more related to your apparent need for a cable connection to activate the wifi?

Is this the first time you have seen the problem or does it always do this trick when you remove the cable and reboot?  Very weird, I agree, whichever situation brings it on.

---

### Post by rfsquared on 2009-07-11
Well, the problem first arose after I had put it to hibernate.  Now it just does it all the time.

Whenever the computer as been on standby, hibernate OR shut down and the wifi isn't working, you have to plug in an ethernet cord.  You immediately get "eth0 connected" and then "2wire451 connected" (that's the name of my network).

But if you try to do it without plugging in the ethernet cord first, if you go up to the connection options by wireless it says "Device Not Ready"

---

