---
title: "Internet Access great, flakey one-way LAN access"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by PlaceboMessiah on 2011-10-11
cablemodem (2 ip's) + i7MacbookPro + P4 UbuntuBox ---> Gigabit Switch

• Internet speed checks out perfectly at 50Mbits on both machines.

• file xfer speed to mac from P4 maxes out at 300KB/s despite gigabit NIC's throughout.*

• Mac can "see" the P4 and shows it in the sidebar of the UI, but cannot remote desktop into P4 from mac... although it goes through the motions of connecting/logging in but never quite makes it.

• Installation of "Personal File Sharing" resulted in this (updating accomplished nothing):

[IMG]http://dl.dropbox.com/u/10478471/Screenshot-Personal%20File%20Sharing%20Preferences.png[/IMG]

• cancelling a file xfer from the linux side induces some kind of network catastrophe and this is the result of attempting to reattach by doubleclicking on the mac's network icon:

[IMG]http://dl.dropbox.com/u/10478471/unknowntype.png[/IMG]


* would also like to employ jumbo packets to use the linuxbox as a NAS, alas setting the MTU to 9000 on either machine makes the situation even worse

---

### Post by Nostalos on 2011-10-11
sounds like tcp window scaling problems to me.  But that is just a wild guess. I have had similar problems with Windows Vista/7/Server2008 and Linux as well.   Differing implementations of RFC1323 do not play nicely together.  Suggest trying to disable it on both MAC and Linux boxes and giving it a try.

[http://lima.osu.edu/ots/tb/200711011550%20_Mac_OS_X_and_Linux_TCP_Window_Scaling.htm](http://lima.osu.edu/ots/tb/200711011550%20_Mac_OS_X_and_Linux_TCP_Window_Scaling.htm)

---

