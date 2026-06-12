---
title: "Wireless card can see the AP but will not connect."
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by steve04 on 2009-01-14
Hello,

I just installed Ubuntu 8.10 and am having some trouble with wireless.  The wireless card I have is LevelOne WNC-0301.  When i click on the network button at the top I can see my AP (the bar next to it varies from about 25%-75%).  When I tell it to connect, it shows the 2 circles with the circle going through them when it is trying to connect (one of the balls turns green but the other never does).  It then says "The network connection has been disconnected."  Any ideas how to fix this problem?  Thanks!

---

### Post by wareagle on 2009-01-14
Does your AP use MAC filtering?  Does it have DHCP enabled (most do by default).

Go to a console session and type this:
sudo iwconfig wlan0 essid "your essid"
sudo dhclient wlan0

Substitute wlan0 for the interface of your wireless network, if necessary.  (Type ifconfig for a list of network interfaces)

---

### Post by steve04 on 2009-01-14
Thank you for the quick reply.  Yes the AP does use MAC filtering.  I was in Windows when I checked the message so when I booted back into Ubuntu (to enter those commands) my computer automatically connected to the AP..  Unfortunately the connection is varying from 5%-100% connection.  One second it will be a 5% then literally 3 seconds later it is up to 35%.  Then it may jump to 100% before going back to 5%.  I don't think there is a problem with the card or AP because I get 100% connections in both XP and Vista.  Any ideas?

---

### Post by steve04 on 2009-01-15
Bump.. anyone have a clue whats going on?

---

### Post by wareagle on 2009-01-15
Does the card work, even though the signal strength is being reported sporadically?

---

### Post by steve04 on 2009-01-16
Yes I can access the Internet but it runs pretty slow.  When downloading a file it will speed up (at times of good connection) and slow down at times of bad connection.

---

### Post by steve04 on 2009-01-17
bump

---

### Post by steve04 on 2009-01-20
I am still having this issue... :(

---

### Post by wareagle on 2009-01-21
See this thread: [http://ubuntuforums.org/showthread.php?t=712935](http://ubuntuforums.org/showthread.php?t=712935)

---

### Post by steve04 on 2009-01-27
> **wareagle said:**
> See this thread: [http://ubuntuforums.org/showthread.php?t=712935](http://ubuntuforums.org/showthread.php?t=712935)


I looked at that link but the link to the drivers for this card no longer works.  It just takes me to the main forums page.  I am having a differnet problem now though... my wireless has atleast worked (although it had a bad signal).  Today when I turned on my computer it won't even connect to my AP at all.  I know my card is good and the router is set up right because I am on the same computer right now (unfortunately using Vista).  Why would this suddenly now work?  Nothing changed from last night to today... :(

---

### Post by steve04 on 2009-01-28
Wireless is back but it is still going from 9-95%.  I really need some help on this issue :(

---

### Post by Brain-free on 2009-03-20
There is a guy with a similar problem in [this]("http://ubuntuforums.org/showthread.php?t=1092356") thread. You might want to consider using ndiswrapper to configure this card correctly.

---

