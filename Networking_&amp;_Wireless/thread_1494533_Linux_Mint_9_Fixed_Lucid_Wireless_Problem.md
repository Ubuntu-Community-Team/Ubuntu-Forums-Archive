---
title: "Linux Mint 9 Fixed Lucid Wireless Problem"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by 1roxtar on 2010-05-27
I have a Dell Optiplex GX150 using a Netgear WG111 v3 dongle for wireless connection.  It works flawlessly with Karmic with no drop in connection ever.  With 10:04 Lucid Lynx, my wireless connection drops and reconnects in an endless loop and I cannot find one single solution to fix it.  I've tried Google-ing and various forums.

I tested Linux Mint 9 since it is based off of Ubuntu 10.04 and what do you know, it works perfectly.  My question is....if the people over at Linux Mint can fix this wireless problem, why can't Ubuntu/Canonical fix it?  

:confused:

---

### Post by rhyz on 2010-05-27
Do you get asked for password for network after about a minute?

If so im having the same problem I've been looking for weeks and nothing. So i have now had to switch back to 9.04 i have seen a lot of posts people having the problem but no fixes its a pain!

I think i might have a look at Mint might work better :)

---

### Post by 1roxtar on 2010-05-27
I don't have to put the password over and over because I have it set to connect automatically.  I had tried several patches, backporting wireless drivers, even trying to install Karmic drivers, but nothing fixed my problem.  I'm gonna keep Linux Mint 9 on this particular computer until Ubuntu solves this problem.  It seems like no one has a real fix for this issue and it's driving me nuts.  Mark Shuttleworth needs to give the guys at Linux Mint a phone call and see what THEY did to fix the problem.

---

### Post by pmenefee on 2010-05-27
I took your advice, but no joy for me.  I have the same problems as 10.4.  Won't connect at all with WPA or WEP, and will only stay connected for about a minute on unsecured site.  I downloaded Mint 9 DVD.  Surely there's no difference in the CD version?

Update:

Instead of just trying to connect on the wireless page where you pick an unsecured network or a hidden network, I clicked on "create new network" and put my WPA information in and it connected almost immediately.........but no data transfers.  I show a connection, but no web page loads, and that's on secured and unsecured.  BTW, the unsecured connection started working (says working, but no data transfer) after I created a network connection on my secure network.  

This is a wireless desktop that I can't plug in.  10.4, and I bet Mint 9 works great when they're plugged, but with no cable in this location, this is a deal breaker for me, and from what I see on the boards many, many others.

---

### Post by keljaden on 2010-05-27
have you guys attempted to use Ndiswrapper to house the windows version of the wireless driver? it will decrease the amount of functionality (no airgcrack-ng i think), but "normal" activity should work just fine.

---

### Post by pmenefee on 2010-05-28
This is old news, but just to confirm what I thought, I downloaded Ubuntu 9.04 and wireless works, sort of.  My network is WPA secured, but there is another unsecured network in the area and that's what is posting this message.  WEP would probably work from what I've read, but that will be the next try.  The WPA connects to the Ubuntu home page but won't load google or yahoo..........strange, and stranger since it's working now.  The unsecured network seems to work fine, at least for the last 5 minutes.  I'll update this version, but no upgrade.  I don't know what they screwed up after 9.04 but it's a mess.

Update:  When I tried to install, rather than just running off the cd, I got an Error 2 problem with Grub.  Could not get around it.  I just happened to notice on another thread that if you had a Raid setup, whatever that is, you must use an Alternate Install CD.  I downloaded it and installed 9.04, and Grub Error 2 went away.  I think I'm done for a while.  As a re-cap, 10.04 would not connect to a wireless connection.  I read, I tried, I copied, I cussed..........and finally just gave up and went back to 9.04.  It connects to my wireless router and WPA2 Personal security with no problem.  When 10.10 comes out, I'll try with a live CD to see if I can connect, but will not upgrade without trying it out first.

---

