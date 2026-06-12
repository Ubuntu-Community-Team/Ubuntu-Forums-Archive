---
title: "Guide in 0.21 sort of locks-up"
date: 2008-03-22
forum: Mythbuntu
---

### Post by Rhiadon on 2008-03-22
No matter what theme I use in myth 0.21, the guide just quits responding. The video window works fine. In some of the themes I get to press keys for a few seconds, other themes I can press keys until I try to scroll the display up or down and then it lock.

This is *not* a hard lock up. If I press escape after the lock it will eventually exit back to live TV but before I does I see a series of rapid movements in the guide as if it queued up all of my keypresses and them executed them.

I'm still running mythbuntu 7.10 and I have upgraded all of the themes to version that are supposed to be compatible with 0.21. (I can enter IMDB numbers)

I know some other people have seen this issue but they hid the fact in another discussion and it was missed. Has anyone fixed this issue. 

I'd particularly like to use the Prject Grayhem theme.

---

### Post by Rhiadon on 2008-03-23
I did a ton more engineering work to try to narrow down what was causing this issue. It is related to the use of any 2x deinterlacer. I can make the guide very slow to respond when any 2x deint. is on and the guide works fine using any other deinterlacer.

I have no idea why a 2x deinterlacer woudl make the guide work slowly. It didn't in 0.20. I've been using Bob 2x ever since I started using mythbuntu and it's been great.

If anybody has any ideas, please share. :)

---

### Post by volkswagner on 2008-03-23
It could be video card drivers.  What is your video card?  Are you using restricted drivers?

---

### Post by Rhiadon on 2008-03-23
It's an onboard nVidia GeForce 6150. Do I need to maybe upgrade the drivers?

---

### Post by volkswagner on 2008-03-24
If you are not using restricted drivers you may want to enable them.  This can be done through mythbuntu-control-centre.  If you are already using the restricted drivers, search your card for other users posts.  I would not recommend upgrading drivers.  This can be painful.  It should be done as a last resort. 



[http://ubuntuforums.org/showthread.php?t=619398]("http://ubuntuforums.org/showthread.php?t=619398")


[http://ubuntuforums.org/showthread.php?t=711591]("http://ubuntuforums.org/showthread.php?t=711591")

This is not meant to scare only inform you of the possible difficulty.

---

### Post by Rhiadon on 2008-03-24
Yeah, I'm using the proprietary drivers.

I tried once before a while ago to upgrade them with disaterous effects. I won't be doing that again anytime soon.

I've come to the conclusion that 0.21 is not quite ready for me yet. I have too many problems with it to make up for the very nice features it added. Deinterlacers are kind of important. But the biggest thing is I can't get my ATSC110 HD capture cards to work in 0.21. I'll just stick with 0.20.2 for a few months yet.

---

### Post by 4dognight on 2008-03-24
> **Rhiadon said:**
> It's an onboard nVidia GeForce 6150. Do I need to maybe upgrade the drivers?

I just upgraded to .21 and have noticed this exact same problem. And, I am also using an onboard Nvidia video( Abit AN-M2 , geforce 7025 ) I have not looked at my deinterlace settings, but I don't think its bob 2x. I am using the restricted drivers.

---

### Post by Rhiadon on 2008-03-24
If you have better luck, please let me know. I'm really wanting to use 0.21 because of several little features they've added and the fact that the new Internal player can play more video types so I don't need to use mplayer.

It's just not stable enough on my system to warrant the upgrade.

Good luck!

---

### Post by volkswagner on 2008-03-24
> But the biggest thing is I can't get my ATSC110 HD capture cards to work in 0.21

What troubles are you having.  I have mine working with Nvidia 6200 card and I posted my video settings here.

[http://ubuntuforums.org/showthread.php?t=726571]("http://ubuntuforums.org/showthread.php?t=726571")

I am only capturing with QAM, not over the air.

---

### Post by Rhiadon on 2008-03-24
Several things actually, seem to be messing up. One could be causing the other so I'm not certain of the root cause.

First, they show up in mythtvsetup as Air2PC cards (which they are not). I know for a fact that I'm loading the right module (saa7134-dvb) and I have the firmware in the correct location.

Second, a third mysterious DVB card shows up as a source (not in mythtv setup but in mythweb) 

Third, I never get video from any of these DVB cards. This is a definate show stopper and trying to figure it out wasn't worth the effort to me at this time.

Of note is the fact that I wiped the system and started from scratch with 0.21 when this occured. Maybe a working 0.20.2 upgraded to 0.21 woudl work fine but the inability to use Bob 2x is also a show stopper.

I'll check out your other thread and see if I can glean any useful information. Thanks for your help so far.

---

