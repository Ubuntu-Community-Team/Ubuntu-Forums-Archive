---
title: "ignoring unknown interface wlan0=wlan0, plus some."
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by Sarteck on 2010-06-11
M'kay, I've got a problem...

I downloaded the Kubuntu 10.04 DVD torrent a few days ago, and installed it on my laptop.  I used the Network Manager to connect to my router, and everything was hunky-dory--it was set up just fine.

However, I have a problem with the update manager (says it couldn't get a lock on /var/lib/apt/lists/lock).  That's a whole 'nother story, though--point is, I tried to come online to get help with it, but Konqueror cannot find Google.

First thing I do is try to ping my router, with the response "destination host unreachable".  :<

Then, **sudo /etc/init.d/networking restart** yields no favourable results, either: **Ignoring unknown interface wlan0=wlan0**

Opening up **/etc/network/interfaces** kind of confused me though--there was no **wlan0** in there--just **lo** and **eth0**.

**iwconfig** shows that it's there, though, with my ESSID and a Link Quality of 70/70, among other things. X3

Strangely enough, KNetworkManager is able to connect just fine to the router--it's just that the rest of the system doesn't recognize that it's connected, somehow. XD







I'm in no rush, so take your time if you'd like to help me out. :)  ATM, I only use the thing for Walkthroughs while I play PS2 (I just got a Tuner Box to allow my monitor to convert the PS2 analog signals to digital so I can play on my monitor, hee hee, it's been fun).  But I just find it weird.



It could be that I screwed something up during install, perhaps?



The card is some kind of Atheros, so it should work with pretty much zero problem on Ubuntu, yah?  S'why I think it's some kind of "Operator Error," heh.  Might be related to my lock on the package manager ****, too.



Anyways, thanks for the time. :3  I'm going to poke it with a stick a few times to see if that helps.  I'll also see if I can get a witch doctor on loan, in case you guys can't help me. XD

---

