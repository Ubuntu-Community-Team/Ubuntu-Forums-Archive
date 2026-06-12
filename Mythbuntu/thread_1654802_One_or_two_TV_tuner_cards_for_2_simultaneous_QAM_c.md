---
title: "One or two TV tuner cards for 2 simultaneous QAM channels?"
date: 2010-12-28
forum: Mythbuntu
---

### Post by mjitkop on 2010-12-28
Hello, I'm considering making my own cable DVR and I am looking for the right TV tuner card.

I've been searching and reading stuff here and there and I know that:

1/ I'll only be able to get a subset of the cable channels (only clear QAM). If I understood correctly from the documentation from my cable company, this means channels 2 - 70. That's fine with me.

2/ I won't have access to On-Demand. I've been living without it already so I won't miss it.

Now I am trying to figure out what TV tuner card to get to be able to:

1/ record 2 different QAM channels at the same time (with no possibility to watch a third one)

2/ record 1 QAM channel AND watch a different one at the same time.

Is there a single TV tuner card that Mythbuntu supports and that will allow me to do what I am looking for? If not, I guess I need 2 cards then?

Thank you in advance for your help.

---

### Post by bcg30506 on 2010-12-28
HD HomeRun.  It is an external ethernet dual-tuner HD QAM/ATSC device that is well supported in mythbuntu.  I love ours.

---

### Post by LowSky on 2010-12-28
HDhomerun is an external option. Haupauge HVR-2250 is a Internal option. There are a few more too. butr these two I think work the best.

Technically you can watch more than just 2 feeds with either card. Digital tuners can record a few more channels as long as those channels share the same bandwidth.

For example for me I can record NBC, CBS, and Fox at the same time because to of the channels are on the same bandwidth.

One thing to really check is how many channels will really be availible. I only get the local broadcast companies without a cable box.

this website can tell you exactly how many channels to really expect, just type in your zipcode: [http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/)

---

### Post by williammanda on 2010-12-29
Basically you are going to need 2 single tuner cards or a dual tuner card. The bandwidth option is icing on the cake. To insure that you will have complete access to more than one channel, you will need more than one tuner. Here is a link to some supported tuners:

[http://linuxtv.org/wiki/index.php/ATSC_Devices]("http://linuxtv.org/wiki/index.php/ATSC_Devices")

---

### Post by mjitkop on 2010-12-29
Thanks, bcg30506. HD Homerun seems very cool. I would have to wire my house for Ethernet though; right now it's all wireless.

LowSky, thank you very much for the technical information. I was not aware of the common bandwidth. Let me see if I understand correctly. Taken from SiliconDust's web site, I can see the following:

```

Channel    Virtual    Name 
111-14        2       WCBS
73-1          2.1     WCBSDT
82-7          3       WFSB    
111-15        4       WNBC
73-2          4.1     WNBCDT 
73-3          4.2     WNBCDT2
73-4          4.4     WNBCDT4 
111-17        5       WNYW
```Does this mean that WCBS, WNBC and WNYW all share channel 111? WCBSDT, WNBCDT, WNBCDT2 and WNBCDT4 share channel 73?

If this is the case, does this mean that I could record WCBS, WNBC and WNYW on channel 111 all at once? Same question with channel 73.

By the way, what program guide understands Comcast's clear QAM channel mapping in my area (Fairfield county, CT)? Could I just select in the guide to record a program on WCBS and another program at the same time on WNBC, and on the other tuner watch a live channel from a separate channel number (WFSB, for example)?

This seems very interesting and exciting now. :lolflag:

Other question: what is the difference between WNBCDT2, and WNBCDT4? Do they play different NBC shows?

I'm pretty sure I can't get OTA channels in my area (bottom of a valley) so only cable.

---

### Post by AKADAP on 2010-12-29
> **mjitkop said:**
> Thanks, bcg30506. HD Homerun seems very cool. I would have to wire my house for Ethernet though; right now it's all wireless.

LowSky, thank you very much for the technical information. I was not aware of the common bandwidth. Let me see if I understand correctly. Taken from SiliconDust's web site, I can see the following:

```

Channel    Virtual    Name 
111-14        2       WCBS
73-1          2.1     WCBSDT
82-7          3       WFSB    
111-15        4       WNBC
73-2          4.1     WNBCDT 
73-3          4.2     WNBCDT2
73-4          4.4     WNBCDT4 
111-17        5       WNYW
```Does this mean that WCBS, WNBC and WNYW all share channel 111? WCBSDT, WNBCDT, WNBCDT2 and WNBCDT4 share channel 73?

If this is the case, does this mean that I could record WCBS, WNBC and WNYW on channel 111 all at once? Same question with channel 73.

yes.
> 
By the way, what program guide understands Comcast's clear QAM channel mapping in my area (Fairfield county, CT)? Could I just select in the guide to record a program on WCBS and another program at the same time on WNBC, and on the other tuner watch a live channel from a separate channel number (WFSB, for example)?

Unfortunately, none.
You will have to go through the channel list and edit the XMLTVIDs for the channels so that you can match up the schedules direct listings to the channels. You may also wish to rename the channels to match Comcasts channel numbers.

Schedules Direct is the way to go for schedule information on MythTV. It costs $20/year, but is is reliable. Broadcasters usually include schedule information in their broadcasts that MythTV can use, but cable companies tend to strip that out. Even when you do get the broadcast schedule, it tends to be unreliable.
> 
This seems very interesting and exciting now. :lolflag:

Other question: what is the difference between WNBCDT2, and WNBCDT4? Do they play different NBC shows?

I'm pretty sure I can't get OTA channels in my area (bottom of a valley) so only cable.

---

### Post by mjitkop on 2010-12-29
Thank you for the link, [williammanda]("http://ubuntuforums.org/member.php?u=235887"), this is very useful information.

AKADAP, thank you for your answers, this is very interesting. Once you have set up Schedules Direct and the XMLTVIDs, the program guide is smart enough to allow you to record channels that share the same bandwidth? (Sorry, I'm all wrapped up around this now)

I'm also looking forward to the availibility of HD Homerun Prime that will include CableCARD. Good things to come.

It's funny, my wife and I were just talking about this subject earlier because she was asking about cable DVRs. Comcast charges $14.95 / month / DVR. She said to forget it. :lolflag: I told her I may be able to make a DVR for cable that will have more recording hours than the DVR from Comcast and with the possibility, in some cases, to record more than 2 channels at once. I think I am on my way to gaining a positive wife acceptance factor. :guitar:

---

### Post by newlinux on 2010-12-29
> **mjitkop said:**
> Thank you for the link, [williammanda]("http://ubuntuforums.org/member.php?u=235887"), this is very useful information.

AKADAP, thank you for your answers, this is very interesting. Once you have set up Schedules Direct and the XMLTVIDs, the program guide is smart enough to allow you to record channels that share the same bandwidth? (Sorry, I'm all wrapped up around this now)
. The mythbackend knows which stations are on the same multiplex. you have the set the number of virtual tuners each card has (the number of shows it can tune simultaneously on the same multiplex) when setting up the tuner card. Default I believe is 2
> 
I'm also looking forward to the availibility of HD Homerun Prime that will include CableCARD. Good things to come.

It's funny, my wife and I were just talking about this subject earlier because she was asking about cable DVRs. Comcast charges $14.95 / month / DVR. She said to forget it. :lolflag: I told her I may be able to make a DVR for cable that will have more recording hours than the DVR from Comcast and with the possibility, in some cases, to record more than 2 channels at once. I think I am on my way to gaining a positive wife acceptance factor. :guitar:

I'm not holding my breath for true cable card functionality in Myth/Linux. If it ever comes to fruition it will probably be limited to copy freely stations, which aren't enough for me, and not much of an improvement over QAM in my area.

---

### Post by AKADAP on 2010-12-30
> **newlinux said:**
> . The mythbackend knows which stations are on the same multiplex. you have the set the number of virtual tuners each card has (the number of shows it can tune simultaneously on the same multiplex) when setting up the tuner card. Default I believe is 2


I'm not holding my breath for true cable card functionality in Myth/Linux. If it ever comes to fruition it will probably be limited to copy freely stations, which aren't enough for me, and not much of an improvement over QAM in my area.

If you must record "copy never" content, the HD-PVR will work, but you must rent a cable box to go with it. When they start to disable the component outputs, you will need the HDFury.

---

### Post by t4thfavor on 2010-12-30
I like the HDHomeRun idea as it is networked, and therefore accessible to more than one client, such as a windows box.

I would also recommend you get something that can tune the digital channels on the cable (kinda like the ATSC 12-1 style channels from over the air) I get about 200 cable channels over the wire without a box, and some are even in HD.

Have fun.

EDIT: I have to admit, I never counted, and quit after 108-20...

---

### Post by newlinux on 2010-12-30
> **AKADAP said:**
> If you must record "copy never" content, the HD-PVR will work, but you must rent a cable box to go with it. When they start to disable the component outputs, you will need the HDFury.

I must, and that is one reason why I have an HD-PVR :) (with satellite however, not cable). When the time comes I see and HDFury2 or 3 (or whatever is available then) in my future.

---

