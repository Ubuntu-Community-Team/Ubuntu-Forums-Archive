---
title: "Unplug - Plug LAN"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by Don DeGregori on 2011-04-26
Just put 10.10 on a Asus eeeBox PC, Mpdel 1007. All is well, except one thing. I don't get an Internet connection unless I unplug the RJ-45 LAN cable on the computer and then plug it back in. I have checked the cable, changed to different port on router. Every single time, if I unplug and re-plug, I get a connection. Internet comes right up. Looking around on Google and this forum,this problem is not unique. I think it is a Realtec problem The NIC cannot be changed for it's on board. 

Is a fix available? I could install 10.04. Will I have same problem? 
donde

---

### Post by BertN45 on 2011-04-26
Is there any differenc before and after unplug/plug, if you compare the data shown in Connection Information menu of the network applet (icon)..

---

### Post by Don DeGregori on 2011-04-26
Yes, for sure. After I boot, with LAN cable plugged in, "Connection Information" is greyed out. After, I unplug/plug LAN, "Connection Information" is fully populated and LAN network is available

Before I wrote here, I tried this:  sudo aptitude remove connman from a suggestion on this forum. No joy. From the responses, it fixed for many, a similar problem I have, but they not using the same computer.  

Now I can't put back connman using Synapic, but problem still is is same.
donde

---

