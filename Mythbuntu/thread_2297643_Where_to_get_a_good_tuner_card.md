---
title: "Where to get a good tuner card?"
date: 2015-10-05
forum: Mythbuntu
---

### Post by spyderdyne on 2015-10-05
I have a media center computer running Ubuntu 15.04 Vivid.  It has 12TB of disk space (LVM) and is backed up to Crashplan with unlimited backup space with 15Mpbs up/ 75Mbps down.  I run Kodi on it and access my media files through Kodi on Roku boxes throughout the house using the Plex media browser application.  We recently replaced Dish Network with Sling ($20 per month,) an HDTV antenna ($65,)  already have Netflix ($7.99 per month,) and have added Hulu ($11.99 per month.)  This is a pretty complete solution, but I need to be able to record the off-air networks to my media center and decided to use MythTV since there isnt really a better solution and it pairs with Ubuntu nicely.  I have installed and configured MythTV to save to a "Recordings" directory and configured Kodi to use it as well.

To achieve true over-the-air freedom I need a tuner card.  After a fair amount of research I settled on the Hauppage 2250 dual tuner device.  It has been around for a long time and many people have had good success with it.  Unfortunately Hauppage decided all the 2250 cards were bad and supposedly issued a recall.  After purchasing what I was told was a 2250, it turned out to be a 2255 model.  These cards are now supported in Linux kernel 4.2 and the drivers are included there, but we arent there yet, and both MythTV 0.27 and 0.28 refuse to work with this card on those kernel versions so I sent the card back, downgraded my kernel, and am stuck.

The list of supported devices on the LinuxTV is very small, and none of the PCIe devices on it are available anywhere.  In fact, even devices that arent on it yet are no longer available for purchase.  I am really interested in one of these now,

> [http://www.tbsdtv.com/products/tbs6704-atsc-or-clear-qam-quad-tuner-pcie-card.html](http://www.tbsdtv.com/products/tbs6704-atsc-or-clear-qam-quad-tuner-pcie-card.html)

...but I cant find one of those anywhere either.  It seems like when the analog to digital switch happened these things were everywhere, and now you cant even get them.

Does anyone know of a good PCIe ATSC tuner card with at least a dual tuner that works with MythTV that is actually being sold somewhere?  We are on the cusp of a tremendous thing here, but I simply cannot find the parts to complete it.  Please help.  I cant even count how many football games I have missed already this season.

Thanks.

---

### Post by TheFu on 2015-10-05
Not what you asked for, but the HDHomerun tuners are completely awesome! The flexibility is amazing NOT to be putting HW into a system - they are network tuners. Extremely well supported. Plus the newer models have DLNA servers, so any DLNA client can be used  to watch live TV.

I've had 2 of their dual tuners for about 3 yrs now. Wouldn't ever go back to a PCIe/PCI/PCIx slot card.  My recording OS runs inside a VM - much harder to do that  with physical cards required.

---

### Post by spyderdyne on 2015-10-06
I really wanted an internal PCIe or PCIx1 card to take advantage of the 12TB of SSHD space.  I dont think anyone ever even made PCIx1 cards for this purpose, and all the compatible PCIe cards are out of print now except for the updated Hauppage cards that arent usable any more.  I may have to go with an external device.  Do the HDHomerun tuners support iSCSI or just SMB based shares?

To clarify, my interest here is DVR functionality.  I have 7 flat screens hooked up around the house to live broadcasts, but can only watch 1 program at a time and can't skip the commercials.  I also try not to let the time a show comes on have any bearing on when I have time to watch it and rarely if ever care to put something else aside for a T.V. show.  The Roku devices running the Plex client to Kodi work very well and the interface is easy to deal with on a simple remote.  I just want MythTV to capture at least 2 programs, scrub the commercials, and save them to disk so Kodi can serve them.  Adding DLNA servers would be ok, but lack of massive local storage on the tuners and having multiple DLNA servers on my network makes things messy and more difficult to manage.

Thanks.

---

### Post by TheFu on 2015-10-06
HDHR are tuners. Nothing more.  That is how I think of them. They just happen to be outside the physical machine.

1 HDHR device (depending on the model) would provide 2 or 3 tuner "cards" to your media recording computer(s). There are different models with different capabilities like OTA ATSC or CableCARD.  
They do not have storage.  
They do not "record" anything.  
They  are just tuners available on the network for any client on the network to use to get TV signals from.

Clients can be 1 MythTV backend or 20 different devices. I've used Win7 Media Center and NextPVR with mine.  Since the current generation provides DLNA servers, any DLNA client can be used to "watch live TV" by using 1 of the tuners.

They are not video recording devices that you can hook up to any video output and record. They are strictly TV-tuners.

Also, no need to use the DLNA servers, if you don't want.

Update:
My house is similar to yours for media.  The only "live tv" we watch is 1 college football team.  Everything else is recorded.  I have 1 plex media server that streams all the media, regardless of where it is stored on the network here. Most is local, but not all. Have 2 Kodi/OSMC machines, 1 Roku, 1 WD HD Live and 1 Chromecast.   Barely use the chromecast or Roku. Roku is for Amazon Prime Video and pretty much nothing else. The raspberry Pi v2 with OSMC runs 18+ hrs a day in the den with either video or music playback - mostly music. Everything is wired that can be. Wifi is used only when there isn't any way to use wired connections.  The core network is GigE.

The HDHRs are 100base-tx - which is more than enough for (2) 1080i streams per device.

We have 1 TV, but it isn't connected to the antennas. The only content is gets is from some other "smart device." The other screens are monitors, tablets or a projector (100 inch screen).

[http://lifehacker.com/five-best-tv-tuner-cards-1600439009](http://lifehacker.com/five-best-tv-tuner-cards-1600439009) - explains the HDHR.

And just 1 more thing. No need to spend more than $85 on one of the dual tuner models. They have sales monthly somewhere.

---

### Post by spyderdyne on 2015-10-06
I'm convinced.  I found one of the older (non-DLNA) dual tuner models on ebay.com for $50 and bought it.  It will be here Friday.  I also found a second one and placed a bid on it.  I also found the setup instructions for MythTV here:

> [https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Dual#MythTV_Setup](https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Dual#MythTV_Setup)

I still have feelers out to see if I can find a real Hauppauge 2250 card, but this definitely seems to solve the problem elegantly and I doubt i will need one now.  

Thanks for your help.

---

