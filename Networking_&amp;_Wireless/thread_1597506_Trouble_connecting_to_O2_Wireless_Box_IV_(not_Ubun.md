---
title: "Trouble connecting to O2 Wireless Box IV (not Ubuntu specific)"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by sixfoottallrabbit on 2010-10-15
[This is a cross post from another forum. It's not exactly Ubuntu specific but I'm hoping I could get some help over here.)

Hey,

I'm having trouble connecting to the O2 Wireless Box IV that was provided with my O2 broadband connection which I bought a couple of weeks ago.

And to help demonstrate the issue, I've recorded a screencast. Note: I recorded this in Ubuntu, but **the same problem exists in Windows 7**.
[http://www.youtube.com/watch?v=iJ3d3Wz7ddo](http://www.youtube.com/watch?v=iJ3d3Wz7ddo)

Parts in the video:
1 - I try connecting to the wireless connection a couple of times
2 - I show the output from lspci in the console
3 - I plug in to the router by ethernet and ping google.com to show that the Internet works fine when wired.

I'm sharing a house with 3 other people, each with their own laptops and one with a wireless printer and I have an Android phone. They all connect pretty fine (with only a few minor hiccups).

The issue I'm having is with my laptop. It's a Dell Inspiron 1545 with a Broadcom Corporation BCM4312 802.11b/g wireless network adapter.

The router is shown in the list of available networks most of the time with an almost full signal, but still I can't connect. If I restart my laptop, it usually connects for about a minute and then just drops out. From then on I just can't connect at all.

However, I am much more successful with connecting when everybody else in the house is out (The reason being less wireless devices connected, I presume).

If I wire up to the router by ethernet then my connection is great but that means I have to be next to the router to access the Internet, which isn't so great.

So for some reason, the router appears to be favouring everybody else's connections over mine. I have no idea why it connects for about a minute when I first boot up.

I repeat from above, this is happening in both Windows 7 and Ubuntu 10.04 exactly the same.

Any help? I've tried to be as thorough as possible, but if you need anything else then just ask.

Thanks.

---

### Post by alexfish on 2010-10-15
hi

can only advise looking here

[https://help.ubuntu.com/community/In...nectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

doub't if some members will look at youtube , eating up there download policy , or other restrictions

alexfish

---

### Post by eddier on 2010-10-19
try setting your Router to use WEP instead of WPA.

I spent Hours trying to get my system to connect,set my router(an O2 wirelessbox IV) to use WEP and it worked on both my laptop and my PC.

It leaves me thinking my shoelaces are undone though!

eddier

---

