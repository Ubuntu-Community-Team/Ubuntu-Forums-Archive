---
title: "Goofy testing notification ???"
date: 2010-08-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-08-13
I've been expecting a notification for 10.04.1 testing for some time. In fact I have both a Karmic and a Hardy ready to try the upgrade, along with trying iso-testing, but I see it's been held back twice now which is fine.

Then today I get this:

> 
From:
"QA Testing Tracker" <qatracker@stgraber.org>
Add sender to Contacts
To:
[email]lbsolost@yahoo.com[/email]

You are receiving this email because you have been subscribed to the
following test case:

Ubuntu Desktop i386 [20100813.3]: [http://iso.qa.ubuntu.com/qatracker/info/4410](http://iso.qa.ubuntu.com/qatracker/info/4410)
Install (auto-resize): [http://iso.qa.ubuntu.com/qatracker/result/4410/9](http://iso.qa.ubuntu.com/qatracker/result/4410/9)
Install (entire disk): [http://iso.qa.ubuntu.com/qatracker/result/4410/5](http://iso.qa.ubuntu.com/qatracker/result/4410/5)
Install (manual partitioning): [http://iso.qa.ubuntu.com/qatracker/result/4410/7](http://iso.qa.ubuntu.com/qatracker/result/4410/7)
Live Session: [http://iso.qa.ubuntu.com/qatracker/result/4410/3](http://iso.qa.ubuntu.com/qatracker/result/4410/3)

Since it's in quote tags the links may not work so here's a copy:

[http://iso.qa.ubuntu.com/qatracker/info/4410](http://iso.qa.ubuntu.com/qatracker/info/4410)

No one's home :confused:

Of course they shouldn't be.

Can anyone tell me what's up? Maybe just a goof?

Or something someone needs to know about?

---

### Post by ronacc on 2010-08-13
someone hit "reply all" instead of "reply":lolflag:

---

### Post by ranch hand on 2010-08-13
If you go to the ISO test team page there is a 10.04.1 test page up.  If you, like me, go to the 64bit desktop live page and then click on the download button there you get an error page.

I do not know about the notification but they may try to do it next week.

I want to see if I can boot the bugger.  I could deal with that.  Be a nice change.

---

### Post by ktp on 2010-08-13
> **ronacc said:**
> someone hit "reply all" instead of "reply":lolflag:

everyone has done that one in life...if you have not you are missing out. :lolflag:

---

### Post by ranch hand on 2010-08-14
Either or they are using plymouth to send those messages as well as the boot messages and log info.  Seems to work about that well.

---

### Post by ranch hand on 2010-08-14
This really is weird.  There appears to be a test of the 64bit desktop manual install started.

There is no ISO that comes up though.  Mentions that the unavailable image is 201013.3.

That image is available but so is one for today.

I have no idea what to do here at all.  Not even sure that I care.  This looks to me like it works as well as the LTS  does for me.  Waste of time probably.

---

### Post by kansasnoob on 2010-08-15
Hmmm, this is a bit odd :confused:

That one was for Lucid and today I got one for Maverick:

> You are receiving this email because you have been subscribed to the
following test case:

Ubuntu Desktop i386 [20100815]: [http://iso.qa.ubuntu.com/qatracker/info/4414](http://iso.qa.ubuntu.com/qatracker/info/4414)
Install (auto-resize): [http://iso.qa.ubuntu.com/qatracker/result/4414/9](http://iso.qa.ubuntu.com/qatracker/result/4414/9)
Install (entire disk): [http://iso.qa.ubuntu.com/qatracker/result/4414/5](http://iso.qa.ubuntu.com/qatracker/result/4414/5)
Install (manual partitioning): [http://iso.qa.ubuntu.com/qatracker/result/4414/7](http://iso.qa.ubuntu.com/qatracker/result/4414/7)
Live Session: [http://iso.qa.ubuntu.com/qatracker/result/4414/3](http://iso.qa.ubuntu.com/qatracker/result/4414/3)

Please report any bugs you identify in Launchpad and report on the
success or failure of the test in the tracker:
[https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/)

Please see the testing team wiki pages for for further information:
[https://wiki.ubuntu.com/Testing](https://wiki.ubuntu.com/Testing)

For questions about the procedure or to coordinate testing, please join
#ubuntu-testing on freenode.

Thank you for helping us to test Ubuntu.

[http://iso.qa.ubuntu.com/qatracker/info/4414](http://iso.qa.ubuntu.com/qatracker/info/4414)

I see from the changelog that we are getting some ubiquity updates every day :D

---

### Post by ranch hand on 2010-08-15
If you copy paste the address for the ISO I bet it will work.   I downloaded the 64bit desktop ISO early this morning using the index to get to the build for the 15th (not the current link) and the address was identical to the one that doesn't work on the test page.

I believe that their link is just bad.

Had to go chase cows on a strange ranch.  Strange in the way it is run, the guy that owns it and my familiarity with it.  They were all in a nieghbors hay field tearing up bales.  Don't know these folks at all.  Not pleasant.  Horse and dog really enjoyed it though.

I am going to burn it and try to test it in a bit.

---

### Post by kansasnoob on 2010-08-15
> If you copy paste the address for the ISO I bet it will work.

Nope. Tried that :)

I really only care about the 10.04.1 because our next official round of Maverick testing shouldn't be until about August 30th, although I will be trying daily's before then just to "learn" the new ubiquity behavior.

ATM I can only imagine that this new ubiquity was tested on nothing but VM's :(

I personally detest the use of VM's for testing because it simply does NOT show what the effects will be with actual hardware. It is however handy for things like taking screenshots of certain behavior, etc.

I am particularly concerned about 10.04.1 because of certain grub bugs. I wish I could also test Wubi but for some reason my old XP won't allow it.

I certainly won't beat my brains out over something Win related :D

---

### Post by ranch hand on 2010-08-15
> **kansasnoob said:**
> Nope. Tried that :)

I really only care about the 10.04.1 because our next official round of Maverick testing shouldn't be until about August 30th, although I will be trying daily's before then just to "learn" the new ubiquity behavior.

ATM I can only imagine that this new ubiquity was tested on nothing but VM's :(

I personally detest the use of VM's for testing because it simply does NOT show what the effects will be with actual hardware. It is however handy for things like taking screenshots of certain behavior, etc.

I am particularly concerned about 10.04.1 because of certain grub bugs. I wish I could also test Wubi but for some reason my old XP won't allow it.

I certainly won't beat my brains out over something Win related :D
That is interesting.

Downloaded from>[http://cdimage.ubuntu.com/lucid/daily-live/20100815/lucid-desktop-amd64.iso](http://cdimage.ubuntu.com/lucid/daily-live/20100815/lucid-desktop-amd64.iso)

Where they say it isn't>[http://cdimage.ubuntu.com/daily-live/20100815/lucid-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/20100815/lucid-desktop-amd64.iso)

There has been one test reported for the Alt-install 64.

---

### Post by ronacc on 2010-08-15
hasn't been a new daily for several days at least not that I could find .

---

### Post by ranch hand on 2010-08-16
[http://cdimage.ubuntu.com/lucid/daily-live/](http://cdimage.ubuntu.com/lucid/daily-live/)

---

### Post by VMC on 2010-08-16
> **ronacc said:**
> hasn't been a new daily for several days at least not that I could find .

Ubuntu Lucid 10.04.1 dated 08/15/2010 found [here]("http://cdimage.ubuntu.com/lucid/daily-live/20100815/"), and Kubuntu found [here]("http://cdimage.ubuntu.com/kubuntu/lucid/daily-live/current/").

Edit: Your right. Those above are for daily-live. daily hasn't been updated in a couple of days.

---

### Post by ronacc on 2010-08-16
Thanks guys , I should have specified Maverick . hasn't been a new one of those since 8/12 , new one this AM , 8/16 though . maybe the new installer will actually work this time .

---

### Post by kansasnoob on 2010-08-16
Got a more sensible notice about 10.04.1 today:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

> We are currently testing candidates for Ubuntu 10.04.1. See testing procedures for details.
Please, take into account that the build links are not working, as we are testing the stable release
The Lucid daily images can be found at [COLOR="Red"]**[http://cdimage.ubuntu.com/lucid/](http://cdimage.ubuntu.com/lucid/)**[/COLOR] 

I kind of wonder if they'll have a round of official upgrade testing from both Hardy and Karmic to Lucid (10.04.1) :confused:

When I'm done with this iso-testing I'll have to do some checking :)

---

### Post by kansasnoob on 2010-08-16
All completed well. I'd immediately like to thank the mods for not moving this since it largely, but not altogether, effected 10.04.1 rather than Maverick :D

IMHO Ubuntu's testing is what sets it apart from all other distros. I'll grant you that I hardly win every battle waged, for instance - you still have only 3 seconds to figure out what those two "emblems" mean on the initial gui screen, but with a complete redo in the works for ubiquity it's wait-n-see time :D

This summer's been hard for me because I've had too little time to play, hopefully soon that will change :)

---

