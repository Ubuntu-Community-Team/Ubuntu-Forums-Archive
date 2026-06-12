---
title: "Network manager doesn't detect wireless anymore"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by @B6Mwu8fN9M on 2009-03-05
System:

Windows Vista
Wubi Intrepid
Intrepid 

My problem is this. Network manager won't detect any wireless networks. This happens on both Intrepid and the Wubi intrepid even though I haven't used the Wubi install for more than 2 months. Windows has not problems so I'm guessing it's not the network card. 

When I click on the network manager applet it shows that wired networks: Auto eth0.. and the wireless networks title with nothing under it. When I installed Wubi, I had no problems and even in the Intrepid install there were not problems up to a week ago. 

Here's something else that's interesting: When I boot into vista than go into Intrepid, the network manager detects all the networks nearby but cannot connect to any of them. It changes the password I put in for my network into a different one that is twice as long as mine. It cannot even connect to an unsecure network.

Attached is the output of lspci -v

---

### Post by sanderj on 2009-03-05
Is your wifi kill switch in the right position during boot?

What if you boot a live-CD: is the wifi then OK?

---

### Post by @B6Mwu8fN9M on 2009-03-05
There are no problems with the wifi on a live CD. It all works fine. 

There is no switch on the laptop. there is a light that can be tapped to turn wifi on and off but it only affects windows. On Ubuntu it has no effect. 

Here's the other problem I'm noticing:
My normal network password: 20784933917500625207849339
Gets turned into: 83d8d95fd59c36ba839535bbbba11b60dd190d77df8381aabaeb4f3651111ec8 
after I type it in.

---

### Post by @B6Mwu8fN9M on 2009-03-05
nevermind, the network manager seems to start displaying networks and all works well. 

The problem with the password changing still persists but I'm posting that to another thread. :popcorn:

---

