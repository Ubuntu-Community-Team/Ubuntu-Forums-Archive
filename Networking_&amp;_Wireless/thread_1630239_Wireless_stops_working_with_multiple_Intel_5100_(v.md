---
title: "Wireless stops working with multiple Intel 5100 (vaio) on wifi"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by futuresandwich on 2010-11-24
Okay this is a slightly weird one. 

I'm using a Vaio TT, which seems to use an Intel 5100 WiFi chipset, and a Linksys WRT54G2 (firmwares 1.0.1 and 1.0.4), ubuntus 10.10 and 10.04. 

Wifi works fine out of the box. However if the other vaio tt in our office (running windows 7) comes online, my laptop stops being able to make new connections. It WILL stay connected to chat servers, and downloads SOMETIMES continue to work. However all new HTTP requests / ssh connections / rdp connections / pings fail. The laptop still appears to be "connected" to the wifi network.

This may also happen after an undetermined amount of time without the extra vaio. It is not solved by reconnecting or rebooting. Once the extra vaio leaves the building, everything works fine again. This problem does not happen at all if I boot into windows.

Can anyone help me diagnose or fix this problem? I'm loving ubuntu so much it's really frustrating that I essentially cannot use it all day at work.

---

### Post by grahammechanical on 2010-11-25
My guess (it is only a guess) is that both Vaios are using the same radio frequency to access the wireless network and one (not your one) is near to the wireless point and therefore it is grabbing the bandwidth.

regards.

---

### Post by futuresandwich on 2010-11-25
Thanks for the suggestion; I wish it were this simple but it's not. Again, the problem only occurs when I am running Ubuntu, and occurs irrespective of position relative to the router. As I understand it the radio channel is set by the router anyway right? So it should be the same band for everyone on the same network regardless.

This weekend I may try and replicate it on a different router just to narrow things down, but all I have around is an OpenWRT flashed WRT54G which is pretty close to the WRT54G2 that we're already using so I'm not sure it'll be that informative.

Anyone know of any diagnostics I can run to figure out exactly what is failing here?

---

### Post by futuresandwich on 2010-11-27
Ok yeah, unsurprisingly using the WRT54GL the same thing happens.

Does anyone have some commands I can run to get a more detailed diagnostic of what EXACTLY is failing here? It doesn't happen in win7 so it's def a software prob.

---

### Post by futuresandwich on 2010-12-05
More more diagnostics: DOES work for a little while after other Vaio is turned on in the same room. Maybe a few minutes.

ifdown/ifup solves it for a couple of minutes before it craps out again too. 

PLEASE if anyone can at least shoot me some commands to get a more detailed diagnostic that'd be appreciated

---

