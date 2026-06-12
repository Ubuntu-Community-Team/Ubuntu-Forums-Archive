---
title: "Ndiswrapper installs 1.55 instead of 1.56 on 10.04"
date: 2012-07-28
forum: Networking &amp; Wireless
---

### Post by Drawdecirle on 2012-07-28
Just to give some background as to what I'm actually trying to do in case there's an easier way:  I've got the Netgear N300 Wireless USB Adapter, model WNA3100.  I've already found numerous forum posts describing in detail how to fix it, but unfortunately, none of them have worked for me.  I've tried just about every driver I can find, bcmwlhigh5, bcmwlhigh6, bcm43xx64, etc. all to varying levels of success.  (The bcmwlhigh6 seems to be the best because it actually shows "hardware present" when I have it plugged in, but I'm still not getting anything to show up when I do "iwconfig".)  However, one thing that seems to be common is that most people are using 1.56 of ndiswrapper-common (-utils).  What I have is 1.55, so I figured this might potentially be the issue (I'm running thin on ideas.)

Yet, when I removed ndiswrapper (ndiswrapper -v could not find ndiswrapper), and make and make install the 1.56 version that I downloaded, ndiswrapper -v shows up as 1.55 still.  I'm using Lucid Lynx (10.04) 64-bit, so will 1.56 just not work for me?  I'm curious to know where it's getting 1.55 if I don't have it anymore.  Any help would be greatly appreciated.

---

