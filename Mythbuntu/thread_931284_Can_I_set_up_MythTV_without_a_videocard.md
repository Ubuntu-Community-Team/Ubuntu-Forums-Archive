---
title: "Can I set up MythTV without a videocard"
date: 2008-09-27
forum: Mythbuntu
---

### Post by Billsputters on 2008-09-27
As the title says, can I set up MythTV without a videocard.

Why? Well, I want to do a quick setup, and get it all going, and show the capabilities to the boss, before we invest in hardware!

So far, I have a working system, I can play videos, music,look at the weather etc. I don't have a capture card for the system, and they are difficult to get here in Uganda! What I have will be a composite video signal input from a DSTV decoder.

 What I really want to get working next is the XMLTV part with the channel listings, but this stalls at 50%. Am I correct i thinking that you need a video card to setup channels before you can grab listings.

---

### Post by ian dobson on 2008-09-27
Hi,

I don't know if this will work, but if you setup a video source, and xmltv grabber/configure your channels manually you should be able to get some of MythTV working.

Maybe just tell the system you have an V4L tuner card and configure it in your video source, MythTV will complain that the card doesn't exist but it should be enough for MythTV to allow the grabber to run.

Regards
Ian Dobson

---

### Post by Billsputters on 2008-09-28
Thanks for that, that seemed to work - it's enabled a lot of menus not seen before.

Now, all I have to do is grab TV list for South Africa via XMLTV. But it freezes at 50% for some reason. Any clues on this one?

---

