---
title: "Internet Connection becomes inactive"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by lsToronto2008 on 2009-06-24
I am pretty new to Ubuntu. So far I love it. But I notice that if I leave my computer connected to the internet for a while it goes into some sort of zombie state where it can't connect to the internet. The connection is good, I have tested it with other machines. I am using a wired connection, the mother board's built in card. I just bought a new card to try in case it is a driver issue. Does anyone else have any tips? I am running 8.03.

Thanks,

Luke

---

### Post by MaindotC on 2009-06-24
Your network card is going into some type of power-saving mode.  I don't have much info on your machine, so here are some general tips.

1.  Check the BIOS settings.  See if there's anything related to a power-saving mode in conjunction with your network card.

2.  Check power settings when you log into your machine.  On mine, I can't see anything that commands the network card with respect to power, but you may have something in your power settings or if there's a restricted driver installed for your network card.

3.  Check syslog - look for the time when your network card "goes to sleep".  It's in System -> Administration -> System Log.  There are a bunch of logs in there but look for the time when it goes dormant.

4.  You can add an applet to your desktop bar that will override power settings for your network card.  Right click the bar at the top of your desktop and click "Add to Panel" and you'll see the icon down the list.

Let us know if you find anything.

---

