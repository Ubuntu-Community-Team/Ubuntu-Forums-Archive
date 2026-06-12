---
title: "Help! I need a new tuner!"
date: 2014-03-08
forum: Mythbuntu
---

### Post by itlarson2 on 2014-03-08
Could anyone who has installed a tuner for US ATSC (digital OTA) in the past year please tell me what they are using?  It needs to be pcie, or usb 2.0.  I was using a Dvico dual tuner, but it died, and the Haaupauge single tuner I replaced it with only lasted a few months.  Fortunately my old pchdtv-5500 still works so I have at least one.

---

### Post by TheFu on 2014-03-09
Go network based!  The HDHomeRun HDHR dual tuners completely rock and don't limit use to a single computer - any PC on the network can use any open tuner.  I had multiple USB/PCI tuners previously - I'll NEVER, NEVER go back.

---

### Post by itlarson2 on 2014-03-10
Networked sucks for my use case.  My Mythbox is an all-in-one system in a HTPC type case, which sits in my livingroom in a stack of A/V equipment, connected to my only TV.  The TV antenna cable comes in the front of the house, but the router is in the back, so whichever place I put the hdhomerun, it will mean stringing cable. It will use my last Ethernet port, which I need sometimes, and it's another box to find a place for and another power brick plugged into the wall.  In short, it's a great piece of hardware, but not for my application.  

I am looking at a Haaupauge usb tuner.  I think I might just mount it to a D-bracket to convert it into an internal device.  I prefer everything to be internal, but anything I put in the pcie slot gets baked by the video card and dies eventually.

---

### Post by TheFu on 2014-03-11
Sorry, got no good recommendation.

I own a Hauppauge 950Q - barely ever used it. On some systems here the USB connection was flaky and the tuner was less than great. At the time, it didn't integrate with MythTV and I didn't have a good antenna system setup to get lots of OTA stations.

Also own a Hauppauge 1512 - not really useful for TV.

 I've come a long way since playing with that tuner both OTA and with ClearQAM.  For me, the COAX runs are much harder than CAT5e ... so switching to ethernet ASAP is best.  I've thought about using power-line networking to extend to far parts of the house. Haven't had the need yet, but it is better than wifi.

---

### Post by tbsoft2001 on 2014-03-11
+1 I, too, am interested in a tuner card that works without hours of configuration. Sadly, I have the Hauppauge HVR-2250 - and, despite efforts two years ago and recently, has never worked with Mythbuntu - or any other mythtv version. Works fine with Windows 7 Media Center first time, every time. Granted, I could just bag mythtv - and perhaps I'll do that.

Meantime, I'd like to know the make, model etc. of a tuner card with two tuners that is compatible with mythbuntu - and by compatible I mean when configuring the mythbuntu back end, the card shows up on the first try and I can set up channels, etc., without the insane trouble people have posted about in this forum. I have pcie and pci slots available.

Thank you in advance and best of luck.

---

### Post by tgm4883 on 2014-03-13
When I was doing digital cards, I think I had a pcHDTV 5500 and an HVR-1600 (or was it an 1800). I'd have to check when I get home, I believe I still have them in a box somewhere.

---

### Post by itlarson2 on 2014-03-13
Despite everything on the Internet saying it should, the 950q dosn't work.  When I channel scan, it is very slow and doesn't find any channels. Yes, I did install the firmware.  I'm debating returning it or pestering the dev who makes the driver.  I anyone knows anything about this tuner, help would be appreciated.

I've ordered an older Avermedia Volar usb tuner, since the new version doesn't work with Linux.  Also I have ordered a pci expansion card, which should allow me to use both of my pchdtv-5500 cards, instead of just the one.  Those are great cards if you can find them, and have the pci slots for them.  With luck I should be back up to three tuners like I was before my Dvico fusion 7 card died.

---

### Post by jeffshearman on 2014-03-28
Here, Here!  I will NEVER go back.

Just way to versatile

---

### Post by sdowney717 on 2014-04-02
Avertv Combo PCIE(M780)
I bought used on Ebay.
It works, but you must install 

sudo apt-get install linux-firmware-nonfree

for the file ngene_15.fw to be put into /lib/firmware.

It then works both in me-tv and mythtv.
All I had to do was select in myth that tuner card and learn how to setup mythtv.
It was the first in the list, came up with an odd name.
me-tv just scanned it and worked quick.

---

