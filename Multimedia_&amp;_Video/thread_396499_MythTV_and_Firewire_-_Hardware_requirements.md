---
title: "MythTV and Firewire - Hardware requirements?"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-03-29
I've been utterly unsuccessful in getting MythTV to record from my analog cable box (see: [http://www.ubuntuforums.org/showthread.php?t=382607](http://www.ubuntuforums.org/showthread.php?t=382607))

Now, Comcast has decided to try to squeeze a little more money out of its customers by eliminating analog cable entirely in Chicago.  To watch pretty much any non-broadcast channel, a digital box will be required.  Since I can't record these channels, my MythTV setup that I have spent months on will be useless in about two weeks.  In order to salvage what I have done, I intend to order a cable box with a firewire port.  I have seen this (incredibly complicated) guide:
[https://help.ubuntu.com/community/MythTV_Edgy_Firewire](https://help.ubuntu.com/community/MythTV_Edgy_Firewire)
What I need, though, is suggestions for hardware.  I don't have a firewire port on my current MythTV backend.  I do have an old PIII with firewire on the motherboard.  Is the firewire transfer a CPU intensive process that would be too much for the old computer to be used as a slave backend?  I'm currently using the system as a remote frontend, so it seems to me that if it is fast enough to play mpeg streams from the backend, shouldn't it be fast enough to capture mpeg streams from the cable box?

If it is too much, then can someone suggest a cheap firewire port that is known to work with Linux and MythTV.

Thanks

---

### Post by majoridiot on 2007-03-30
i'm sorry you found the firewire guide complicated- i tried to make it as straightforward and
explanatory as possible.

i would certainly try the PIII as a slave backend for for firwewire-only streaming... it should have
sufficient power to handle that. as far as a firewire add-on, you should be pretty safe with any
card from a known manufacturer.  i believe the card i purchased was an A-open or such... somewhere
around $15-20.  no need for anything fancy- one port will do... although you will probably find
cards with 2-4 ports.

btw... which STB is comcast offering?

feel free to pm me for assistance if needed- i'm happy to help you work out firewire config.  :)

---

### Post by josesanders on 2007-04-06
Sorry, I didn't mean to imply that the firewire guide was *unnecessarily* complicated, just that it looks like a complicated process.  I very much appreciate you creating the guide, especially given the complexity.

It seems that the only suitable STB that Comcast has to offer is the one that they have for their DVR, which would cost an extra $11 per month plus $40 installation, so I'm going to consider that option a last resort for now.

---

### Post by majoridiot on 2007-04-06
> **josesanders said:**
> It seems that the only suitable STB that Comcast has to offer is the one that they have for their DVR, which would cost an extra $11 per month plus $40 installation, so I'm going to consider that option a last resort for now.

the DVR option is pretty much the standard with different cable suppliers if you want digital channels
and firewire.  $11 isn't too bad- my service charges $15.

save the $40 install and pick it up yourself.  "installation" consists of plugging it in and hooking the
cable to it... literally.  they automatically synch on power-on to retrieve auth. info, guides, firmware, etc.

there is really no acceptable reason for them to insist on them having to install it, nor charging $40 to
do it.  push them. :)

---

