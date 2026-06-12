---
title: "Understanding Contemporary MythTV"
date: 2013-02-23
forum: Mythbuntu
---

### Post by Elaphe on 2013-02-23
Hi all! I apologize in advance for being so clueless, but I'm hoping someone here will offer me some help as I'm under a bit of a time restraint....

Years ago I used to use a MythTV system on Ubuntu to capture and record standard definition television using a couple of Hauppauge PVR-150's, and life was never better. Then, I met my wife, and when we moved in together we got a high definition TV, digital cable with something approaching a DVR solution, and somehow the MythTV system got left behind. Years later now both my wife and I have seriously grown tired of the limited capacity and versatility of the cable company's DVR, and we really wish we had an alternative. So I began revisiting the idea of using MythTV to record digital cable, but I find myself overwhelmed with all the new hardware and lingo. Additionally, I'm finding a lot about what *could* be done, but I'm hoping to find out what's really been working for people, particularly those who share my cable provider, if possible.

So here's what I need help with, please: I have returned to school, and I have a break coming up in mid March, and that's when I believe I'll have the time to put a MythTV system together, and get it working (at least a basic system). In the meantime, I'm hoping to find out what hardware I'll need, and get that ordered up in advance. By hardware I'm specifically referring to what I need to capture TV broadcasts, and get them into MythTV, not so much the "guts" of the system, so tuner cards or devices, video cards, sounds cards, and remote controlls that work well with MythTV. Any advice or help anyone can offer me would be VERY MUCH appreciated! I'm willing to do lots of reading and research on my own, I just need someone to help streamline my efforts so I understand what kind of a setup I need, and where to find info on setting up such systems.
[B]
Here's more info about what we have, and what we hope to be able to do:[/B]

We live in the United States, in Upstate New York, and our cable company is Time Warner digital cable. We are concerned mostly with recording high definition programming from the "upper" digital channels such as Discovery, Home and Garden Network, Animal Planet, etc. We are NOT interested in recording programming from pay channels such as HBO, Cinimax, or Showtime., etc. We get nothing more than the most basic digital package.

We have one company provided cable box with DVR (an SA Explorer 4280 HDC) and the corresponding remote control. That STB is connected to our fairly new Samsung HDTV in our living room, and we have access to HD channels from 1000 on up, except for the channels you'd pay extra for (like HBO). Additionally, we have a fairly new Samsung HDTV in our bedroom without a cable box, it gets just the basic channel 2 through 70 or so channels you get when you simply connect the coaxial cable wire from the wall to the back of the TV.

What we'd like to be able to do is recorded digital TV shows from the cable box in the living room, and then have them available on both TV's. I know I can use a master back end in the living room, and a slave front or back end in the bedroom, but I really don't know what hardware people are using to capture HD programming these days. Can I use a Hauppaugue HD PVR unit, or a cable card arrangement, or what? How can I find out what the easiest and most successful setup is for others using Time Warner Cable in our part of the Northeast US?

Could someone please help me get going on this MythTV project? I'd really like to get the basic system assembled and running over my break from school in mid March so then my wife can watch all her favorite shows when I'm stuck in class late nights. Again, I'm more than willing to do my own reading, but I'm so busy with school right now that I can't possibly sift through all the information in time to find out what I'd need to get going, and so I'm appealing to the Ubuntu community for guidance and advice.

Thank you in advance for your help!!!

-Elaphe

---

### Post by BicyclerBoy on 2013-02-23
Might I suggest you check out
[http://www.mythtv.org/wiki/CableCARD](http://www.mythtv.org/wiki/CableCARD)
& mythtv mailing list archives
[http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)
most posters are North American..

Time Warner are fingered as be problematic in flagging everything as restricted copy..

All NA cable providers are moving to encrypt/flag protect all content, even free OTA channels relays (with FCC approval).

There has been posts here (mythbuntu) about cablecards etc..

You might be pressing the old PVR-150 into use..

---

### Post by Elaphe on 2013-02-23
Hi! And thank you for your reply!

So, are you suggesting I won't be able to do much more than record standard definition? What about these new [Hauppauge HD PVR units]("http://www.hauppauge.com/site/products/data_hdpvr.html")? I got the idea that I could somehow use one of these, am I wrong?

Thank you!

-Elaphe

---

### Post by BicyclerBoy on 2013-02-28
The mythtv mailing list archives is a mine (or minefield) of info about this type of issue..& there have been recent discussion about ceton cards etc..
The Nth American TV market appears very complicated from outside..

My limited understanding:
To record HD thru' the analogue hole, the STB has to output HD on component. This is increasingly less likely & some analogue outputs use macrovision protection.
You can test using your TVs component inputs..(disconnect the HDMI cable).
You may find that later model STB is worse/more restrictive.

To receive/record thru' a cablecard your provider has to (allow cablecards &) set the correct flags on each stream..
Time Warner are indicated as flagging everything as "not copy freely".

I was under the impression that direct connection of your "cable" to TV was functionality that is being removed.
AFAIK a tuning adapter/STB/cablecard is soon to be required by all..(No free OTA relay over cable in the clear).
The FCC allowed this.
Possibly I'm being alarmist..

---

### Post by newlinux on 2013-03-01
If your area has copy flags set to copy once or copy never for any of those channels a cable card solution isn't for you. some set top boxes allow you to check this for each channel via a special menu. if your cable box outputs HD via its component outs, you can use an HD-PVR. I have an HD-PVR and it works great for recording 720P and 1080i. I also have an HD Homerun and an HD Homerun Prime (cable card) and I still get local HD in clear QAM (HD Homerun) and some of the upper channels with HD Homerun Prime (cable card). For cable provides what's available digitally varies greatly and is sometimes ever changing from location and provider to different locations and providers.

---

### Post by Elaphe on 2013-03-02
Sorry about the late reply, but I did check, and my STB does have component out. So I think I'm going to look into the HD-PVR and see what I can do with that. Thanks for the replies and help, I very much appreciate it!

-Elaphe

---

