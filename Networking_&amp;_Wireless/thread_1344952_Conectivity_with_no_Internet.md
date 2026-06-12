---
title: "Conectivity with no Internet"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by Wombat101 on 2009-12-03
[FONT=Arial Black]I have recently started having troubles with my wireless and internet.  I connect to my wireless routers and access point but I can't get out to the internet. I'm also able to ping the network.  My wife can access the web with her Windows laptop, so I know I haven't ruined the internet connection (to be explained).  When I boot windows, I have the same problem, so either my hardware (broadcom 43xx wireless adapter) is bad or the drivers have been corrupted (in  a cross platform sense? I find this hard to beleive).

The details on the whole system and network.
Laptop: Dell Inspirion 5150 with Pentium 4
            Dual booting Windows XP and Xubuntu

Home Network:
Main gateway router is a Belkin F5D7230-4
Wireless Access points are a bricked F5D7230-4 (broken reset button) and an Actiontec WT701-WG.

In an attempt to fix my intermittent wireless connection, I turned the Actiotec DSL Modem into an access point by activating the transparent bridgeing and placed it near my work place. Past attempts have ruined all ability to cocnnect to the wireless (wrong bridge settings). This solution worked breifly.  My signal strength went from 50% to 91%.  The next day, all signal strength was lost and back to an intermittent 50% and 70% (I never moved away from the Actiontec).

When connected by CAT5 I have internet.  It is with this conection that I am writing this thread of desperation.  This means I have no ip conflicts on the router (my desktop laptop have two different IP's from several different means of connectiog to the network).  Is this a bug in the wireless configurations or is my wireless adapter finally dead (the laptop is 6 years old)?

Update:
It would seem that my Actiontec DSL modem turned access point might have been causing for trouble for my laptop. Restarted my laptop  this morning and had internet.  The only difference being that the Actiontec was turned off.  After turning it on and trying to connect, I lost all internet even though I was able to ping my gateway and other network computers. I still troubleintermitent wireless connections, but I assume that's due to the relatively weak signle that is being registered by network manager. Still doesn't explain what the jolly is going wrong since my wife has no troubles with the access point being on, but all will be revealed.
[/FONT]

---

### Post by Wombat101 on 2009-12-05
Problem Solved!  I activated the DHCP on the Actiontec and that was causing a conflict of interests for the network..

---

