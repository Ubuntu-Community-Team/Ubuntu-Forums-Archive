---
title: "Wintv-PVR-500 (hauppauge!)"
date: 2008-12-06
forum: Mythbuntu
---

### Post by thafemann on 2008-12-06
Hey there,

After months of wrestling and frustration with 8.04 I finally got things working with 8.10.  Yeah!

Now, to take it a step further.

I know that I can play live TV on the monitor connected to the computer.  I can play a recorded movie through the network.  Haven't figured out LIVE yet.

Now, the hard part.  This is a dual head card.  Not really sure what that means anymore.  :)

I want to somehow hook this into my real tv.  There doesn't seem to be any out put, only INPUT devices, and MANY of them.  FM, Cable, and two sets of composite Video and R and L.  

Is there no way to get output?

Also, I read somewhere where I can use the SVideo output from my Pioneer Cable box to the input of my controller.  Haven't figured that one out yet.  

Also, How do I statically assign an ip address of the mythtv box.

TIA

Tom

---

### Post by ian dobson on 2008-12-07
Hi,

Dual head card just means that you have 2 tuners onboard so that you can record 2 channels at the same time.

The PVR-500 doesn't have an output. The output is from your VGA card. 

You need to define 2 inputs in myth-setup to be able to use both tuners. To record from your Pioneer Cable box you need to wire up the s-video out from the pioneer to the s-video in on the PVR-500 and configure mythtv to use the s-video-1 input.

You should be able to configure a fixed IP address with the network manager.


Regards
Ian Dobson

---

### Post by thafemann on 2008-12-07
Gotcha!  :)  Wonderful,  and oh crap! all at the same time.

So, I spent way too much on this card that has no Output, right? :(

So, I am pretty sure that this was discussed someplace else, but....

Is there a card with an output that is going to be good to go on Feb 17th?

When I use the output from the S-Video from the Pioneer system, all I get is the channel that the Pioneer is tuned into.  I assume that is correct.

With MythTV and Ubuntu, I assume that all I am going to get is the standard 2-99 channels?

Tom

---

### Post by ian dobson on 2008-12-07
Hi,

Whats so special about the Feb 17th?

Yep you'll only get the channel that the Pioneer is tuned to. If you want to change the channel on the Pioneer you'll need to use a "IR Blaster".

Regards
Ian Dobson

---

### Post by I-75 on 2008-12-07
> **ian dobson said:**
> Hi,

Whats so special about the Feb 17th?
Regards
Ian Dobson


"On February 17, 2009 all full-power broadcast television stations in the United States will stop broadcasting on analog airwaves and begin broadcasting only in digital. Digital broadcasting will allow stations to offer improved picture and sound quality and additional channels. Find out more about whether or not you will be impacted by the digital TV (DTV) transition. "

[http://www.dtv.gov/whatisdtv.html](http://www.dtv.gov/whatisdtv.html)

---

