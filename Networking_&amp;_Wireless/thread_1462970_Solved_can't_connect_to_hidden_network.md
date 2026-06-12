---
title: "Solved: can't connect to hidden network"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by tenbob1 on 2010-04-26
Hi. I'm a complete n00b who just installed ubuntu 9.10 on my Fujitsu Amilo Li1705 laptop. 

I just wanted to share how I got my wireless network working after spending several hours doing it wrong. It might be helpful to others.

My wireless router is set up as a "hidden network". That is, it doesn't broadcast the SSID to prevent hackers. My laptop connected fine under Windows, but not Ubuntu.
Lots of posts told me to do stuff in the Network Manager. I tried, but I couldn't find the right settings. It turns out there are *TWO* different programs that control the network settings. I was using the wrong one.

To get to one of them you go to System/Preferences/Network Connections. This program is *NOT* Network Manager. Whatever I tried to set up in this program, I could not get a working connection. 

The other program, the *REAL* Network Manager, is a different program altogether. You get to it by clicking the network icon at the top right corner of the screen. The problem is you can barely see it if the network is not working. When the network is down, all you can see is a tiny greyed out triangle. That's the thing you have to click. 

After I clicked this and followed the steps under "Connect to a hidden network"  I was able to connect just fine. 

It probably seems obvious to regular users. But it took me a while to figure it out. Hope this helps.

---

### Post by Iowan on 2010-04-26
Probably not really necessary, but...
[[SOLVED]]("http://https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

