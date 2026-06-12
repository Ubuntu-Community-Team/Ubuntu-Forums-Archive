---
title: "airlink 101 AWLH 3028"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by dagarshali on 2009-03-20
Hi,
i have posted in this very same forum yesterday and so far I haven't gotten any response and I haven't been able to solve the problem by reading various resources on the web.

When I do lspci, I do see the card. I installed ndiswrapper and used the net8185.inf do install the driver. The driver that i picked was in the windowsxp folder of the airlink cd. I have come across some documents on the web which tells us to use the .inf file for windows 98. does that matter?

However, when i use the net8185.inf from the xp folder and install, i see that in the ndiswrapper that the hardware present:yes . all the websites that I came across say that if you see that as yes, then it is installed properly. 

I set my router first to wep security. I connected to the network without problem. but it doesn't connect to it after some time. I have the access to a router of my neighbor and it doesn't connect to that either:(

Then if i remove the driver and reinstall it, it connects again for sometime and then disconnects.

I then changed the security to wpa and the result was same.

then i changed the settings on the router to allow this particular mac address of the card and the result is the same.

I kernel that i have is x.x.x.27. I have ubuntu 8.10 installed.

when i do iwconfig, i see that the chipset is realtek 8185.

I really would appreciate any help to fix this particular problem

Thanks a bunch in advance

Cheers,
vishwa

---

