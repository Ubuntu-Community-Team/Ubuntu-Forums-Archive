---
title: "Good HDTV tuner card for MythTV?"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by Angryartichoke on 2008-03-17
So I built a sweet Mythbuntu HTPC for my dad, and he's been bitten by the HD bug. He wants to get the local channels thought the media center box now.

I was considering getting a Hauppauge HVR-1600, but I hear the drivers are still crap.

Can I please get some recommendations for some good HDTV tuners? And if it matters, the service provider is Comcast, and I live in Oregon.

---

### Post by Dr Bones on 2008-03-17
I was thinking about building myself a rig as well and I was thinking about getting at least one pcHDTV 5500 cards if not a pair as I had read that the DVB support was supposed to be good as well as built into the linux kernel.  I also read the new release of Mythtv (.21) removed support through the V4linux drivers so don't try and do it that way if you do indeed go this route (just a heads up).  Here is a link to the card in question.  [http://www.pchdtv.com/](http://www.pchdtv.com/)  Hopes this helps start your search at least.:-\"

---

### Post by Angryartichoke on 2008-03-17
Thanks for the quick reply. Anyone else have any input??

---

### Post by cozmicharlie on 2008-03-18
The November 07 issue of CPU magazine has a good section on building a HTPC box using Linux.  It's good because they give you info on what tuners etc work well in Linux (at least in their experience).  You can check it out here [http://www.computerpoweruser.com/Editorial/TOC.asp?guid=B6B0A328564D4D0F8450EE669AE39682&iid=1191](http://www.computerpoweruser.com/Editorial/TOC.asp?guid=B6B0A328564D4D0F8450EE669AE39682&iid=1191)

This is what they say about TV tuners:  Some TV tuners are a generation behind with regard to Linux support.  This is their list of tuners that they like and the one they ended up using.

WinTV-HVR-1800  -  was not supported under Linux though Hauppauge said one was in the works - check [www.linuxtv.org](www.linuxtv.org) for announcements.  It appears that support for the 1800 is still not available though some support shows up in this table [http://www.linuxtv.org/wiki/index.php/Hauppauge](http://www.linuxtv.org/wiki/index.php/Hauppauge).

WinTV-HVR-1600 - this is supported now under Linux and may be what you are looking for [http://www.hauppauge.com/site/support/support_faq_linux.html](http://www.hauppauge.com/site/support/support_faq_linux.html).

The Hauppauge WinTV-PVR-350 is the one they used.  However, the bundled applications did not work so they used MythTV instead.  They also used the tutorial here (tinyurl.com/ypkktf)to get it to work.  I did not see on the Hauppauge site that it supports HD though.  

linuxtv.org has lots of good info that you may want to read through.

I hope this helps

---

