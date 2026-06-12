---
title: "how do I test my tuner and cable?"
date: 2010-01-20
forum: Mythbuntu
---

### Post by linuxhippy on 2010-01-20
I just bought a Pinnacle PCTV HD PCI card.  I read that it is supported by mythtv.  I also have mythbuntu 9.10 installed.  When I go to the watch tv menu in that I get a box that states that mythtv or mythbuntu is using the video resources...or something like that.  How can I make sure that my video capture card has been recognized by mythbuntu and how then do I set it up just to watch TV?

EDIT:

Also, I did lspci and didn't see anything that said Pinnacle or tuner card.

---

### Post by linuxhippy on 2010-01-21
Well I found out how to test the card-

lspci -vvnn

should give 3 listings with Pinnacle in them and which modules are being used.  So, my tuner card has been recognized!  

Now, I still cannot get the tuner to tune any stations.  I have a digital antenna which I tried after cable tv to see if that made a difference.  It didn't...the tuner would not scan for any channels.

Could someone please tell me how to tune in some channels with this card.

---

### Post by SiHa on 2010-01-22
Have you setup the backend and added the capture cards?

[http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index)

Particularly Section 3.

Edit: Just looked at section 3. Pretty useless.

Quick summary then, run mythtv-setup:

All settings in the 'general' tab can probably be left at default values.
Add a capture card, (not sure what type the card is, so you're on your own there!)
Then define a Video Source, and finally an Input Connection. In this last stage, you should be able to do a channel scan.

After exiting you'll be asked if you want to run Mythfilldatabase. Say 'Yes'.

Then, hopefully, you should be able to watch TV.

---

### Post by linuxhippy on 2010-01-22
> **SiHa said:**
> Have you setup the backend and added the capture cards?
All settings in the 'general' tab can probably be left at default values.
Add a capture card, (not sure what type the card is, so you're on your own there!)
Then define a Video Source, and finally an Input Connection. In this last stage, you should be able to do a channel scan.

After exiting you'll be asked if you want to run Mythfilldatabase. Say 'Yes'.

Then, hopefully, you should be able to watch TV.

This is what I have done...I get 3 cards that are identified as Pinnacle in Capture Cards (my card is a hybrid) but none scan channels (that option isn't selectable) in Input Conections).  My source is us-broadcast or us-cable in General.  

[COLOR="Red"]Video source is empty[/COLOR]-I'm trying to make an entry called trial since I have a 7 day trial that started today with Schedules Direct.  My username and password are not saving, though.  When I try to add a new video source it won't let me save what's in that screen...it says:

Run xmltv configure command

[COLOR="Blue"]Also, when I run Mythfilldatabase when I exit I say yes and it runs real quick and then closes.  It must have an error because when I go through this process again it again wants to run Mythfilldatabase.  Do I NEED to subscribe to the online tv database that's available?[/COLOR]

---

