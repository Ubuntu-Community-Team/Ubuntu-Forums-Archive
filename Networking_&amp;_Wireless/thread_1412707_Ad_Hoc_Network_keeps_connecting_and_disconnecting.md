---
title: "Ad Hoc Network keeps connecting and disconnecting"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by jl.mendieta on 2010-02-21
I was using an Old LapTop (lets call it Lap 1)to share my broadband connection via an ad hoc network to other 2 laptops, my new laptop and my flatmate's (lets call them Lap2 and 3). everything worked like a charm for some weeks but then after a restart lap1 wouldnt connect to the adhoc network auto matically as it was configured to do, I tried manually and no luck so I created a new ad hoc network and the Network_Manager keeps connecting and disconnecting nonstop for a couple minutes then it shut down  and have to launch it again from the terminal. I have tried everything, that comes to mind. even Un-instaltted and re-installed the Network-manager and nothing seems to work. I ran out of ideas and I can find nothing on the forum.

Can someone please help me?

---

### Post by unteer on 2010-08-06
really bummed there is no response to this. I am having the same problem with a lenovo s9e using ubuntu 10.04 lucid lynx.

OP, have you had any luck in the months since posting?

---

### Post by zengreng on 2010-08-18
Another thread on this problem:
[http://ubuntuforums.org/showthread.php?t=1545617](http://ubuntuforums.org/showthread.php?t=1545617)

If you install both dnsmasq and dnsmasq-basic, it may happen that nm-applet keep disconnecting. Removing dnsmasq solved that problem for me.

---

