---
title: "aircrack-ng ipw2200 with ubtuntu 8.10"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by dafuzzbudd on 2009-04-15
Alright, so I've spent about a week now trying to get this to work.  I'm currently using the intel ipw220 chipset.  

I've found the ipw2200 injection driver but have had no luck installing it.  I think the source of my problem is that 8.10 uses mac80211 while the driver looks for ieee80211.  My attempt at installing the patch failed miserabley.  Installing the ieee80211 source took out my ability to use wireless.  After messing around with it for a day, I found help on some forum that told me to reinstall the ubuntu 80211 packages and that fixed my problem.

After much messing around with aircrack-ng, I've cracked my own network but only because I was connected to it.  I can see my buddy's network and it's activity.  When I try to connect to it with a fakekey, I can generate a couple IV's attempting to connect, but the aireplay always fails. Here are the guide's I've used 

[http://www.aircrack-ng.org/doku.php?id=ipw2200](http://www.aircrack-ng.org/doku.php?id=ipw2200)
installing gives errors at iee80211 sudo make 
[http://www.aircrack-ng.org/doku.php?id=ipw2200_generic](http://www.aircrack-ng.org/doku.php?id=ipw2200_generic)
cracked my own using -3, but doesnt seem to work when im not authenticated. I can find packets when doing -4 but it always fails beyond that.
[http://www.aircrack-ng.org/doku.php?id=how_to_crack_wep_with_no_clients](http://www.aircrack-ng.org/doku.php?id=how_to_crack_wep_with_no_clients)
but authentication always fails.

So right now im running unpatched but rtap0 seems to work properly.  This almost leads me to think 8.10 has a fixed ipw220 driver.

This all leads to my main question:
Can i patch my ipw2200 with ubuntu 8.10?

---

### Post by dafuzzbudd on 2009-04-15
o0o i just found this 
[http://ubuntuforums.org/showthread.php?t=1060324](http://ubuntuforums.org/showthread.php?t=1060324)
will try when i get home

---

### Post by dafuzzbudd on 2009-05-04
I realized i'd generate 10 packets at a time if i attempted a -4 attack.  I made a script to rerun the command every 30 seconds.  during the night i collected 200,000 packets. YES! I use aircrack and it gives me the fake password i used to try and connect, WTH.

I thought I patched my card successfully but I cant get anything from the router.  I guess the problem is i have to collect on a router with an active client.

CONCLUSION: I need a new card.

---

