---
title: "can not connect wireless when using awesome window manager"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by lightmanhk on 2011-05-04
Hello, everyone. As I mentioned on the thread title, I can not connect wilreless under awesome window manager,it can scan wirless, but just can not connect it. I am using
sudo iwconfig wlan0  essid "...."  key s:"***"
or 
sudo iwconfig wlan0 essid "...." key s:****  (I try both, neither of it works)

and I do some search, and trying 
sudo iwconfig eth1 essid "..." key s:***** 
it is not working as well. 

So, hoping you can give any solution. I am appreciating your helping.  

But, interesting thing is, under gnome, it wireless is pretty good, I have no idea how it could be, but just works fine. 

btw, under awesome, when I typing nm-tool, it always indicate that wlan0 is disconnect.

---

### Post by The Geeko on 2011-06-24
I am having this exact same problem.  I installed awesome, and wanted to work through some online tutorials... alas!  I cannot connect to the network.

I'm new to linux... just installed Ubuntu 11.04 (using the windows installer) for testing...

I must say that I am in love with it... but don't care for the Unity interface... (especially don't like not being able to configure the left-dock bar, which from what I have read is NOT ever going to be a user-preference... sounds like somebody has been hanging around Bill Gates... LOL)

So, I have installed awesome window manager... but I'm stuck since my network at home is wi-fi (through my router)... and I have not figured out yet how to connect when under awesome.

Under Unity, there is no problem... since it detected the router and asked me (upon installation) for the password...

I can see that the ifconfig reports differently when under awesome than when under Unity... so I know that this is the issue...

Now, how to resolve it...

If anyone can help, I will appreciate it... otherwise, back to my searching... LOL

==== UPDATE ===================
OK.  I resolved the issue by logging in under Unity... checking the configuration for internet... and clicking the option to "share" connection.

---

