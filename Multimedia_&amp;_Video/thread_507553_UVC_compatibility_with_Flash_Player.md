---
title: "UVC compatibility with Flash Player"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by relix on 2007-07-23
THe UVC-drivers are V4l2. The Linux Flash Player is V4l1 (damn you adobe!). Is there a way to make them work together?

I've heard some things about a v4l1_compat layer which supposedly does what I need to do, but I've never heard anyone tell me it actually works, especailly with the Flash Player.

The reason I ask is because I want to buy one of the new AutoFocus webcams that are around these days (Logitech Quickcam Pro 9000 or Creative Live! Cam Optia AF). They're only supported through the linux uvc-drivers though. I need to be certain of compatibility with the flash player before I shell out $100 on *just* a webcam!

Thanks.

---

### Post by PsychedelicReaction on 2007-07-30
i join the request

---

### Post by priegog on 2007-11-28
Haha, bump, as I'm interested in this matter too.

---

### Post by olavjunior on 2007-12-11
Me to :(

---

### Post by Kheops_74 on 2008-02-16
I have the same problem. I have a v4l2 webcam and i'm not able to use site that use flash. :mad:

---

### Post by priegog on 2008-02-18
So, this is what I did and that I feel we need to do in large numbers in order for adobe to start thinking about linux users.
Go to this page [http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform&product=17](http://www.adobe.com/cfusion/mmform/index.cfm?name=wishform&product=17)
fill out the info, and request that they add support for v4l2/UVC drivers to a future release of their flash player for linux. 
I know it's too much work but, we gotta start making ourselves heard to get linux up to par in "webstandards" to the rest of the OS's. 
Maybe some of you who have blogs can spread the word (or at least write a decent essay on the issue to be able to digg it).
Let's for now use this thread as the HQ for the campaign to get v4l2 support on flash player, unless something better comes along, that is.

---

### Post by anabelle on 2008-03-15
hmmmm, last answer December 2005 i wonder what happened with this?

---

### Post by priegog on 2008-03-15
I think you have the wrong thread, this one wsa created on July 2007.

---

### Post by PsychedelicReaction on 2008-03-15
ahaha we are all subscribed to the thread....however as far as i know nothing happened...

---

### Post by priegog on 2008-03-15
Oh, I get what he got wrong... He thought my Join date was the post's date. Made that mistake quite a few times myself... Anyways, the only option we have is to beg adobe for support. Read my post [here]("http://ubuntuforums.org/showpost.php?p=4355494&postcount=6").
But yeah it seems we are all waiting for an update on this.

---

### Post by anabelle on 2008-03-15
U.U 

Yes I guess I got confused with the join date... sorry.

I already submited a request to adobe, lets wait for a fix soon :)

---

### Post by mweinelt on 2008-04-25
Did take the opportunity as well and messaged Adobe that way, hope they'll fix this soon. V4Lv1 is deprecated anyway :(

---

### Post by wdaniels on 2008-04-28
Note that there is a way to get this working, although it's not perfect:

[The Flashcam Project]("http://www.swift-tools.net/Flashcam/")

I wouldn't waste your time with Adobe, they're pretty useless and don't seem to care about Linux users anyway. We're still waiting for a 64bit version of flash and the Windows version actually seems to run faster on Linux through Wine than the native Linux version (not just my observation)!

---

### Post by priegog on 2008-04-29
hye thanks for the heads up, this actually looks really good.

---

### Post by anabelle on 2008-05-20
Does the new flash player 10 change any of this?

---

### Post by priegog on 2008-05-20
I looked into it... but no, not for now. It's still a beta this might change. But I'm not getting my hopes up.

---

### Post by tk03759 on 2008-06-04
Hey, just came across this thread looking for a fix for stickam.

I sent Adobe an email as well, and I'm about to try the FlashCam Project. ...I hate the get dirty solutions cause I always wind up screwing something else up. =/

---

### Post by donpdonp on 2008-06-11
thanks for the adode bug link. i sent them a report.

the flashcam project is great, it works fine except only 160x120. when i got a 2MP Quickcam Pro for Notebooks. its kind of disappointing to see such low resolution.

---

### Post by anabelle on 2008-07-05
It's suposed to work in flash player 10 beta2 but it isn't for me, it turns the cam on for asecond but it crashes inmediatly. and nothing happenes.

It leaves a process running eating all de CPU...

---

### Post by wdaniels on 2008-07-05
> **donpdonp said:**
> thanks for the adode bug link. i sent them a report.

the flashcam project is great, it works fine except only 160x120. when i got a 2MP Quickcam Pro for Notebooks. its kind of disappointing to see such low resolution.

I seem to remember you can set the size with a parameter somewhere...but let's hope they get things sorted for flash 10!

---

