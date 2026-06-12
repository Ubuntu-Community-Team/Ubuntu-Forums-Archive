---
title: "DirecTV and networking"
date: 2008-01-24
forum: Mythbuntu
---

### Post by kazbear on 2008-01-24
I just set up a mythbuntu box.  Basically using some old equipment.  I have a couple questions and hope someone can help me out.

Everything seems to work right out of the "box".  Here is my setup:

1.8 ghz AMD something
20 gig HD (Mythbuntu installed)
80 gig HD (Planned for saved recordings)
600 or so MB Ram
ATI TV Wonder
DirecTV receiver

So, my plan is to just record from whatever the channel the DTV receiver is on.  I dont care about controlling it with MythTV.

I ham connecting the the Receiver to the TVWonder with coaxial (Out to TV from DTV to the TVWonder)

My initial testing of watching TV shows me a really bad quality picture.  Some noise and a really washed out, too bright image.

I have not tried to connect the SVideo since I cant quite find the right cable.  They both have different connectors.

Is there a setting I am missing, or maybe its not really designed to be connected this way... I can always go into the image settings and adjust brightness and such, but that looks like it would be a bit tedious.  Unless I missed something, it does not look like you can adjust it what looking at the picture (true???).

That's one issue.  The other thing I am wondering is about networking.  I have 2 windows boxes, 1 Ubuntu box (Other then the Mythbuntu box) and 2 Xboxes connected to my network.  I need to get them all working together.

The mythbuntu box used to be an XP box.  I had one XBox connected to it using a network bridge to connect it to my network (Wireless).  Now that its connected to the Mythbox, not sure if I can do the same thing.

I plan on watching any recorded shows through Xbox Media center.  So I guess all I need to do is set up a samba share on the mythbox (?).  But do I need to manually configure ip addresses to match the windows network?  I may also want to access the MythTV database from the other Ubuntu box using a MythTV frontend.

I appreciate your help

-kaz

---

### Post by tgm4883 on 2008-01-24
You will need to activate the samba service in mythbuntu control center.  Then gram xbmcmythtv plugin for mythtv.  I haven't been able to get the live tv working, but the recorded content works great.  You will have to do a few simple commands on your mysql database too, but i dont have those commands on hand.  I will grab and post them when I get home today.

---

