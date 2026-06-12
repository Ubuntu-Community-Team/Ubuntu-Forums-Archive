---
title: "HP dm3 - Atheros Wireless not working after sleep?"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by stoopid_noob on 2009-11-29
Hi guys, 

I just picked up the new, very sexy, HP dm3 ultraslim. I had an Atheros card in my Acer, so I am aware of the issues with these cards. I am at the point of wanting to simply swap the card out for a Broadcom alternative. 

In the meantime I would like to get the wireless working properly. The card is an Atheros AR5009 (which coincidentally isn't even listed on the Atheros website), and it works out of the box after installation of Windows 7 and U9.10. Yay!

Not so Yay! : The wireless doesn't work after sleep mode. When I wake the machine up from sleep it will turn on the wireless, I am connected and then about a minute later it disconnects from my network and won't connect again unless I restart the computer. 

Help!

---

### Post by stoopid_noob on 2009-11-29
Anybody?

---

### Post by koolguynet on 2009-12-08
I have the same notebook and I wish I had a good answer.  Wireless support is horrible for it under Ubuntu.  I can connect after it wakes, but my problem is that it drops about 12% of the packets.  I watch it happen.  It just stops working for 10 or so seconds.  I installed backports which helped 'a little.'  I find it hard to believe that no one much smarter than me has fixed Atheros wireless cards in Ubuntu.

---

### Post by Robert Blafford on 2009-12-12
I have the same exact problem. I dont think atk9k will work with our newer cards

---

### Post by koolguynet on 2009-12-14
This is becoming more than an inconvenience, I don't know how much longer I can put up with this.  Has anyone found a fix?

---

### Post by xouhcoatl on 2009-12-19
Yo! guys I have the same DM3Z laptop. And I had the same problem with karmic koala but after I updated and upgraded today everithing works great. just go to update manager and install the update.

---

### Post by enrich on 2009-12-21
got the same problem on dm3 1010el
do you think it's possible to replace the wireless card with a draft-N one without changing the antenna?

ah btw what about the BT device? is it working on your dm3 (mine isn't, koala can't find the device) ?
if it works do you have the same issue?

thanks

---

### Post by Robert Blafford on 2010-01-22
i've installed all upgrades and nothing is solved. My card will connect to a wireless g router, but it will go out if it wakes from sleep or 20 minutes pass by. It never failes those 20 minutes...but I have windows 7 on the same computer (dual boot) and everything works fine there. We just need the drivers but theres no way to use ndiswrapper with the drivers that hp gives us. Any help!?

---

### Post by meesekiller on 2010-01-31
I have a similar problem. I've had this laptop for a couple of weeks now and it keeps dropping my connection. It seems if the signal strength is less than a certain amount it just drops the connection. Really annoying. I have no idea if there is a fix.

Using Ubuntu 9.10 here.

At first I thought this was a G/N problem...but I am sitting in a building which is suppose to have only an N-wireless network...and it just dropped me after dropping to about 30-40 percent connectivity. The main problem is after that...I can't connect at all. Further, there seems to be a hiccup sometimes in downloads...like it will get to a point and stop for 10 seconds...then continue. I don't know all the technical aspects...but it is really annoying.

---

### Post by stoopid_noob on 2010-02-02
There is no fix, at least not that I have found. There are a few things that should be noted however. 

If you are using wireless N, make sure that you are using WPA2 for your wireless security. 

If your computer never sleeps, the connection will continue to work! (this is a joke obviously, and HP should absolutely have a solution available)

Just so everyone knows, this very same thing happens under Windows 7, so it is not just an Ubuntu driver issue. This is a hardware issue, and HP needs to step forward and resolve it.

---

### Post by stratomaniac1 on 2010-02-04
Are you all running WICD? 

I gave up on Ubu 8.x versions because I couldn't get reliable wireless.  A year or so later, I looked into Ubuntu again and installed Karmic 64, and found WICD.  Works great for reliable wireless except that my Atheros card seems to turn off when my laptop sleeps, and won't turn on.  Either that or I'm losing the router and can't find it.  I can't seem to find a solution either.  Tried turning the card on manually from term...nothing.  Rebooting seems to be the only answer.

I've decided not to let my laptop sleep, and instead let it hibernate or shut it down completely.  Hopefully this will get fixed.  It's more of a minor annoyance than a real problem for me, but I like it when things "just work".

---

### Post by stinkball on 2010-03-15
I have the same problem with my broadcom bcm4306.  an alternative to rebooting is reloading the wireless kernel module.  for me, this is this command:

sudo rmmod b43 && sudo modprobe b43

if you have an atheros card, replace b43 with whatever module atheros cards use.  hope this helps some, and if there is a permanent solution, be sure to let us all know.

---

### Post by Robert Blafford on 2010-04-19
Any new news on these drivers becoming available?

---

### Post by Dukenukemx on 2010-04-26
Someone solve the problem.
[http://swiss.ubuntuforums.org/showthread.php?t=1018178&highlight=sleep+wifi&page=2](http://swiss.ubuntuforums.org/showthread.php?t=1018178&highlight=sleep+wifi&page=2)

Now if someone can so me how to do this with BCM4306.

---

