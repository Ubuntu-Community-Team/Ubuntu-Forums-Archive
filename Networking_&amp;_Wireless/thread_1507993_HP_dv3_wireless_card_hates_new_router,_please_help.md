---
title: "HP dv3 wireless card hates new router, please help!"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by inverseroom on 2010-06-12
A puzzling problem.  I've had this HP dv3 laptop for a while...it has been running 10.4 very smoothly since release, wireless connection has worked great and connected very fast.  Wireless card is Broadcom, I am using the STA driver.

Yesterday our Linksys router died.  I bought a new one, a D-Link DIR-615.  All the other wireless devices in the house love it, but Lucid wouldn't connect.  I'm using WPA encyption, same as with the old router.

I tried blacklisting rt2800usb.  Hooray, it worked!  Except, even though the connection was made and the computer was online, the wireless icon still displayed the exclamation point indicating there was no connection.  strange.

This morning I power up the computer, and once again, it isn't connecting.  So this time I went back into blacklist.conf and REMOVED the blacklist of rt2800usb.  And lo and behold, it connected again--and again, the wireless icon says it's not connected.

Nothing else has changed on my laptop--only the router is different.  Any suggestions?

---

### Post by inverseroom on 2010-06-12
And a brief update, if I may.  Upon reboot, after removing the blacklist, it wouldn't connect.  Then I clicked the icon, tried connecting again, and it worked immediately.  It's not a matter of an inconsistent signal--signal is very strong.  The red exclamation mark is still there.

---

### Post by inverseroom on 2010-06-12
One update more.  When I boot up and Lucid tries to connect AUTOMATICALLY, it NEVER connects.  But the FIRST TIME I try to connect manually, it connects IMMEDIATELY...regardless of whether anything is blacklisted or not.

Any ideas?

---

### Post by inverseroom on 2010-06-18
Thought I'd give this a bump.  I did an apt-get update the other night, and it seems to have made things worse.  Now it usually connects on the second try, but sometimes takes four or five tries.  Icon is still showing me the exclamation mark.

---

### Post by inverseroom on 2010-06-19
Tried getting rid of network manager and installing wicd.  wicd won't connect at all.

---

### Post by inverseroom on 2010-06-19
Another hint.  On all the computers in the house, the wireless printer must be reinstalled EVERY SESSION, otherwise it reads as offline.

Does nobody have any suggestions for me?  I would really appreciate a bit of assistance.  The printer issue makes me think that this has something to do with the firmware settings.

---

### Post by inverseroom on 2010-06-21
Ok, last try.  I am out of town now, and using my laptop on another wireless network.  Not only does it connect immediately, the exclamation mark disappears when the connection happens, just like the old days.  It is clearly a problem with my router settings.

If anyone can help me figure out what settings to apply to my DIR-615 router to make it play nice with Ubuntu Lucid, I would love your help.

---

### Post by coldraven on 2010-06-29
I have a Compaq 6715b laptop with built-in Broadcom wi-fi.
Since a fresh install of 10.04 I get very fast network connection via  wi-fi.
On boot-up or resume from suspend I am online in under 10 secs.
However I always get the red exclamation mark in the network icon.
I don't actually know what it is trying to tell me!!
Hovering the mouse over the connection name, left clicking, right clicking, what do you have to do to get some information about the state of the wi-fi?
Somewhere in this process I did install a new router but as I'm the only user it never occurred to me that this could be something to do with it.
I could swap back to the old router and see if it makes a difference.

---

### Post by inverseroom on 2010-06-29
Thanks for the reply.  I ended up updating the router firmware, and this fixed the connection problem.  But it didn't fix the exclamation mark.  Not sure why one router would cause the exclamation mark and another would not, but this does seem to be the case.

---

