---
title: "How to get the Alfa AWUS036H (and probably other realtek 8187s) working"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by mewrei on 2009-02-13
First make sure that you have the rtl8187 driver installed and loaded by running (do NOT plug your Alfa in yet, if you already have it plugged in, unplug it, disable any existing networking equipment, restart the wireless by right clicking on the network manager and unchecking "Wireless", then recheck it)
```
sudo modprobe rtl8187
```

Now plug your Alfa in.  You should see that the Network Manager identifies the dongle as a "Realtek RTL8187".  Go ahead and associate with a network if you can.

Now I was using the Alfa with an 8dBi antenna.  You do the math to realize how much power that is, and you're probably getting a bunch of reflections and echos.  We need to turn the power down.

```
sudo iwconfig wlan0 txpower 50mW
```

Where wlan0 is the name of your dongle.

I also had an issue where the dongle was identifying the signal strength as much lower than it actually was, so it set my bit rate really low (like 1Mb/s)

To fix this, run
```
sudo iwconfig wlan0 rate auto
```

And it should read 54 Mb/s when you do another iwconfig

Now you need to reassociate to the network.  You do this by going to your network manager and right clicking on the network you've already associated to.

After doing this my networking was screaming fast.  Also continued to work after reboot, but the power went back up.  I left it alone and things seemed stable.  Held a stable ping over 2000 sequences with around 1% packet loss.

Hope this helps.

---

### Post by profster on 2009-02-22
I have a weird thing going on with my Alpha unit.  It seems to work fine but the link quality on all connections is 17%.  I have been linking up various outside connections and my own inside which has a link quality of around 60% with a Linksys Wireless G USB device.  The Alpha is always at 17% no matter what site I connect up to.  I was at my other location where there is a condo highrise and I had about 20 possible connections and they were all reading the same link quality.

---

### Post by gwinru on 2009-02-28
Hi
I have also a problem with my ALFA AWUS036H .
I am a new born on Ubuntu (today :UNBUNTU 8.10 KERNEL 2-6-27-11)
It blink once and that is all.
I don't know and i am afraid to go in the system to do modifications ;
Is there a simple software to download to solve the problem (window style ,it use to work perfectly with XP and Vista)

THANKS

---

### Post by redonwhite on 2009-03-08
> **profster said:**
> I have a weird thing going on with my Alpha unit.  It seems to work fine but the link quality on all connections is 17%.  I have been linking up various outside connections and my own inside which has a link quality of around 60% with a Linksys Wireless G USB device.  The Alpha is always at 17% no matter what site I connect up to.  I was at my other location where there is a condo highrise and I had about 20 possible connections and they were all reading the same link quality.

I have the same problem of my Alfa being stuck at either 16 percent or 17 percent link quality.

---

### Post by gwinru on 2009-03-10
Hi 

Did anybody tested the ALFA in the field .i saw on a french forum that the 16/17 % does not mean anything .The card is OK it might be just the reading that is out of line????

---

### Post by mewrei on 2009-04-11
Its a driver issue.  I had the same issue but mine worked just fine.  If you followed the above directions it should be functioning, just not reporting properly.

---

### Post by oliwek on 2009-10-14
you should read this :

[http://www.aircrack-ng.org/doku.php?id=r8187&DokuWiki=aab8a25818ece2aec503396aba370e9f](http://www.aircrack-ng.org/doku.php?id=r8187&DokuWiki=aab8a25818ece2aec503396aba370e9f) 


then see this patch : (for the 17% signal level issue)

[http://patches.aircrack-ng.org/rtl8187_hw_signal_backport_2.6.28.patch](http://patches.aircrack-ng.org/rtl8187_hw_signal_backport_2.6.28.patch)

---

### Post by ene_dene on 2009-10-19
> **oliwek said:**
> you should read this :

[http://www.aircrack-ng.org/doku.php?id=r8187&DokuWiki=aab8a25818ece2aec503396aba370e9f](http://www.aircrack-ng.org/doku.php?id=r8187&DokuWiki=aab8a25818ece2aec503396aba370e9f) 


then see this patch : (for the 17% signal level issue)

[http://patches.aircrack-ng.org/rtl8187_hw_signal_backport_2.6.28.patch](http://patches.aircrack-ng.org/rtl8187_hw_signal_backport_2.6.28.patch)
How to use these patches?

---

### Post by Throbbing Gristle on 2009-12-29
Yes I have prob with my Alfa AWUS050NH. It only works half the time. Light goes from blinking red to just red then theres no connection? Running 904 Ubuntu on Tosihba lap top Kernel 2.6.28-17-generic . A tutorial on patching would be nice! I get the Idea nobody has a working Alfa if its not working off the bat? Or they just some how got lucky. Runs all day long on my desk top 904 Ubuntu same Kernel? Why..

---

