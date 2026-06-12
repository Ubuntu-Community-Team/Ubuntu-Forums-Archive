---
title: "HDTV recording through component video? (from satellite)"
date: 2008-04-17
forum: Mythbuntu
---

### Post by cecilkorik on 2008-04-17
I have a perfectly working MythTV box right now but I want to add HDTV support and it's absolutely baffling. Hopefully some kind soul around here can help me out.

My plan at the moment is to get a HDTV set-top box from my satellite provider since it seems like that's the only (legal) way to integrate properly to their system. Now, their set top box outputs HDTV on either DVI or component video (YPbPr) as far as I can tell. I know I will also need another IR Blaster to change the channels on the set top box, but I don't expect any difficulty with that.

What I do need and cannot find is a HD tuner card for one of these types of input and I cannot find any that list either one. They all seem to be focused on HDTV over Coaxial... am I going about this all wrong? Are there any tuners that can read either DVI or YPbPr formats?

If someone could recommend some hardware that does what I want (and works well in Linux, obviously) that would be great... or if what I'm trying isn't going to work, does anyone have any other suggestions on how to go about it?

---

### Post by tgm4883 on 2008-04-17
There is currently no card that will do what you want to do.  There is on the horizon(read, end of may) an external box from hauppauge that will encode HD on the fly to mpeg4, although it won't be supported out of the gate in linux. 

Here is the link to the card.  Currently it seems to be missing from the site, read into that whatever you want [http://www.hauppauge.com/site/products/hd_pvr.html](http://www.hauppauge.com/site/products/hd_pvr.html)

As for the IR blasting, i've had trouble with my ir blasting and my directv receivers.  The best option I have found is this thing  [http://www.patersontech.com/products/usbtvtranslator.aspx](http://www.patersontech.com/products/usbtvtranslator.aspx)

It connects via serial/usb and has worked 99.99% of the time.

---

### Post by majoridiot on 2008-04-17
> **tgm4883 said:**
> There is currently no card that will do what you want to do.  There is on the horizon(read, end of may) an external box from hauppauge that will encode HD on the fly to mpeg4, although it won't be supported out of the gate in linux..

according to a post in the mythtv mailing list some time ago, a hauppauge dev was quoted as 
claiming linux support for the HD-PVR at or very near release.

again... for what it's worth ;)

---

### Post by cecilkorik on 2008-04-18
Interesting. That's definitely what I'm looking for but it's knd of surprising that there isn't such a thing already.

I'm glad it' s just around the corner though, I'll keep an eye on it. Thanks for the info.

---

### Post by majoridiot on 2008-04-18
> **cecilkorik said:**
> Interesting. That's definitely what I'm looking for but it's knd of surprising that there isn't such a thing already.

I'm glad it' s just around the corner though, I'll keep an eye on it. Thanks for the info.

i have a very nice component capture card- the blackmagic intensity- which does a fantastic job of HD capping.
the bad thing is that is has windoze/mac-only drivers, so it's of limited use.  it does not include onboard compression,
but the custom codec does compress to RTJPEG, although with filesizes of appx 55GB/hr.

it's great for archiving special HD material that i want to hold on to, but not of much use beyond that.

it's a shame blackmagic won't release info so open-source drivers could be developed.

---

