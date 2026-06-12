---
title: "Preventing Network-manager from asking for password"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by Metz on 2012-10-17
I have an issue where network-manager repeatedly asks for my network password when it loses connection. This wouldn't be an issue, except whilst the connection window is displayed, it is no longer trying to connect, which is ridiculous. This is simply because of weak signals in my house, not becuase the network key has changed. 

The machine is in an inaccesible place, I need a ladder to get to it. So is there a way to prevent network-manager doing this??

---

### Post by kurt18947 on 2012-10-17
I presume the WAP - wireless access point is difficult to reach.  I'm not certain my problem is the same as yours but 12.10 does  this to me.  I'm using a USB adapter - Netgear WNA1100 - Atheros AR9271.  I find if I unplug, count to 10 and replug it'll work. If your adapter is integral, is there a way to power it down via a switch or key combination?  This is an infrequent occurrence for me and 12.10 does seem a bit flaky.

---

### Post by Metz on 2012-10-17
Sadly, as the machine is stored in a loft, I cant access it, otherwise, I'd simply hit the ok button when it asked for the password. As I don't have physical access to the machine, everything it done through SSH. But that's no good to me if the machine has disconnected from the network and won't reconnect because it's sitting there waiting for meaningless user interaction.

---

### Post by Metz on 2012-10-17
This isn't a question of resolving the quality of my connection. That simply isn't going to happen. I realise I'm right at the boundary of signal strength, but for 90% of the time it works absolutely fine. But I just wish it would continue to try to connect rather that popup a stupid and useless window. Is there a way to turn it off?

---

### Post by gerrman97 on 2012-10-17
that is a problem that can be fixed by just moving closer to your router. or move the router itself. if it constantly does that then maybe find a wireless usb adapter for your computer and get an extention for it. i tried it and it worked.

---

### Post by Metz on 2012-10-17
Can't move machine. Can't move router. Can't change wifi card. Just trying to find out if I can change the behaviour of network-manager.

---

