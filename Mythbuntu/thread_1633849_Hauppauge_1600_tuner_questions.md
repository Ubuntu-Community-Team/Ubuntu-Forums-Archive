---
title: "Hauppauge 1600 tuner questions"
date: 2010-11-29
forum: Mythbuntu
---

### Post by CaptainPatent on 2010-11-29
I currently have a Hauppauge 1600 running on Mythbuntu 10.04 and I am currently unsure if the digital side of my Hauppauge card is working. I have tested it with negative results, but I'm unsure of the broadcast standards coming through the coax so I'm not sure if the tests I did are even valid.

Currently my cable (provided by Comcast) is split three ways directly from the wall with one coax line going to each of my cable box, my Cable modem, and my Hauppauge 1600 analog line. The analog channels work perfectly in this setup, however there is (of course) no way to tune to the digital channels.

In the past, I have tried to connect an additional coax from the splitter to the digital side both with and without the analog connection being present but have had no luck tuning to the digital channels through Mythbuntu.

I would like to be able to verify that the digital side does or doesn't work without swapping the machine completely to windows just to test so...

My questions are as follows:
1) Are drivers for the digital side of the Hauppauge 1600 currently supported in Linux?
2) What is the incoming cable standard before and after the cable box and is there any reason the connection before the cable box would not be tunable? (I would prefer to avoid tuning through the cable box if possible) I'm pretty sure the incoming format for the unencrypted channels is Clear-QAM and the cable box converts the current Clear-QAM channel input to the NTSC-compatible channel 3, is this correct? 
3) Is the digital side of the Hauppauge card only capable of tuning Digital feeds from an antenna input? (most of the working setups I've seen are antenna input from the digital side)
-and lastly-
4) If the digital portion of this card is not well supported in Linux, do you have any recommendations for cards that are better capable of Digital recording through a coax input?

Cheers and happy DVR-ing!


*Edit* The reason I'm suspicious the Digital side may not be functional at all is the Beta drivers from Mythbuntu 7.10 and 8.04 caused the card to function improperly to the point that 3 of my frequently used channels on the Analog tuner ceased to work entirely. I would not be surprised if they had a negative impact on the Digital side also. If you have a similar setup that is working with the Digital side, let me know.

[B][COLOR="Green"]*Edit* I have verified the digital side of my Hauppauge card is functional in Linux thanks to the help of people on the forums - rock on! :guitar:

I have one remaining question now: 
Is there a good way to correlate digital channels to a schedules direct account without manually entering all of the channels?[/COLOR][/B]

---

### Post by spydeyrch on 2010-11-29
So I have the same card in my machine. It works fine for me in both windows and linux (ubuntu 10.04 x64)

Here is how I have it setup:

from my wall I have it split twice: one goes directly to my cable modem and the other is split twice: once going directly to my tv and then the other being split twice: one to my analog tuner and the other to the digital tuner of the Hauppauge 1600.

I don't have a cable box, I just pay for local channels because I can't get them over the air.

I have comcast.

From the sounds of it, it sounds like you are going from the wall to your cable box and then from your cable box, splitting it: one to tv and other to pc tuner card. Is that right? Sorry if it isn't.

Maybe you should try going straight from the wall to your tuner card. Granted you wouldn't be able to get the premium channels.

Hope that helps!!

Oh, and this works for me in both linux and windows 7.

-Spydey

EDIT: Have you check out the manufacuter's website? They have linux drivers there. Might help. I just had to plug and go on mine.

---

### Post by CaptainPatent on 2010-11-29
> **spydeyrch said:**
> From the sounds of it, it sounds like you are going from the wall to your cable box and then from your cable box, splitting it: one to tv and other to pc tuner card. Is that right? Sorry if it isn't.

Actually no - it's a single 4-way splitter and this is how it was set up:

Wall ---> Splitter ---> Cable Modem ---> Computer
..........................&#9492;--> Cable Box -------> TV
..........................&#9492;--> MythTV Analog ----^
..........................&#9492;--> MythTV Digital -----&#9496;

The split occurs right out of the wall and the signal from the wall was piped directly to the tuner on both sides.


> **spydeyrch said:**
> Maybe you should try going straight from the wall to your tuner card. Granted you wouldn't be able to get the premium channels.

I'm currently tuning from the Analog side straight from the wall with no problems, but the digital side has never worked straight from the wall.

This is also why I'm curious of the standards because I'm not sure what digital Comcast channels need to be decoded to tune properly. There are a large number of digital channels my TV decodes fine (sans cable box) but Not a single one (premium or not) is decoded by the card.


> **spydeyrch said:**
> EDIT: Have you check out the manufacuter's website? They have linux drivers there. Might help. I just had to plug and go on mine.

I've checked the manufacturer's website and didn't see the Linux drivers, but they're listed as fully supported in 10.04.

The fact they work right out of the box for you is kind of what I was afraid of - I'm getting more suspicious the Digital side of my card isn't working. I'd just like to know a bit more about the coax input feed formats to make sure.


P.S. - Do you happen to remember the MythTV options you chose regarding input format and video source selection for your digital channels?

---

### Post by Chunk of Earth on 2010-11-29
Check [this]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600") out.

---

### Post by spydeyrch on 2010-11-30
So I don't know if this helps or not but.....
comcast transmits their channels in via the ClearQAM format when digital. I played around with my tuner a while back an this is what I got.

If I had the cable connected to just the analog, it would get just the local analog channels. If I had it connected to just the digital and selected the digital provider (granted I am talking about windows right now for the pure format related experience), then I would get just the local digital channels, which were in quantity, less than what I would get with the analog. If I connected just the digital yet selected analog provider, I would get a menu of every single channel that comcast offers (kind of like the menu that shows up on one's tv via the cable box) yet all, except the local, channels would be encoded and fuzzy and full of snow.

If I connected both analog and digital, I was given the option of configuring both analog and digital tuners and therefore got the local digital channels just fine and those that didn't come through, I got on the analog side. Again, this was all done inside windows.

I don't recall at this moment my settings for mythTV, I haven't used it via mythTV for a number of months so I will have to check.

Your digital tuner should be getting at the very least the local channels in digital quality. It sounds to me like you might have a busted tuner.

I would do a process of elimination and try running it on a windows machine. 

-Spydey

---

### Post by spydeyrch on 2010-11-30
> **Chunk of Earth said:**
> Check [this]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600") out.


This has a TON of good info. Hopefully it helps.

Good find Chunk of Earth!!


-Spydey

---

### Post by klc5555 on 2010-11-30
> **CaptainPatent said:**
> I currently have a Hauppauge 1600 running on Mythbuntu 10.04 and I am currently unsure if the digital side of my Hauppauge card is working. I have tested it with negative results, but I'm unsure of the broadcast standards coming through the coax so I'm not sure if the tests I did are even valid.

Currently my cable (provided by Comcast) is split three ways directly from the wall with one coax line going to each of my cable box, my Cable modem, and my Hauppauge 1600 analog line. The analog channels work perfectly in this setup, however there is (of course) no way to tune to the digital channels.

In the past, I have tried to connect an additional coax from the splitter to the digital side both with and without the analog connection being present but have had no luck tuning to the digital channels through Mythbuntu.

I would like to be able to verify that the digital side does or doesn't work without swapping the machine completely to windows just to test so...

My questions are as follows:
1) Are drivers for the digital side of the Hauppauge 1600 currently supported in Linux?
2) What is the incoming cable standard before and after the cable box and is there any reason the connection before the cable box would not be tunable? (I would prefer to avoid tuning through the cable box if possible) I'm pretty sure the incoming format for the unencrypted channels is Clear-QAM and the cable box converts the current Clear-QAM channel input to the NTSC-compatible channel 3, is this correct? 
3) Is the digital side of the Hauppauge card only capable of tuning Digital feeds from an antenna input? (most of the working setups I've seen are antenna input from the digital side)
-and lastly-
4) If the digital portion of this card is not well supported in linux, do you have any recommendations for cards that are better capable of Digital recording through a coax input?

Cheers and happy DVR-ing!


*Edit* The reason I'm suspicious the Digital side may not be functional at all is the Beta drivers from Mythbuntu 7.10 and 8.04 caused the card to function improperly to the point that 3 of my frequently used channels on the Analog tuner ceased to work entirely. I would not be surprised if they had a negative impact on the Digital side also. If you have a similar setup that is working with the Digital side, let me know.

The cx-18 drivers over the last 3 months to a year have been vastly improved. Particularly on the digital side, also on the analog. I have a couple of 1600s that I used exclusively for analog capture off of Comcast DTAs because the digital side was nearly unusable. In the midst of other unrelated upgrades on that particular machine around a month ago, I downloaded, compiled and installed a new daily snapshot of the driver repository at linuxtv.org I also decided to test the digital side of the 1600s for the first time in over a year.

I was astonished to discover that the digital side of the 1600 could now get locks on all of my local Comcast QAM channels except for two HD ones. With a bit more puttering around, I discovered that the problem with the two supposedly "bad" stations was not that the signal was too weak (the former big problem with the 1600s) but rather that the signal was too strong --evidently the digital amplification issues with the 1600 have mostly been solved. Once I took the digital side of the 1600s off my line amp, their reception has been perfect. I now use them (without amp) instead of my AverMedia A180s, because they consistently have a lower bit-error rate than the A180s. 

In any event, my 1600s are hooked to my Comcast as follows:


Cable In >>>4 way split
.............. 1 MBE
.............. 2 MBE 
.............. 3 MBE
.............. 4>>>50 ft. drop to the SBEs >>>4 way split
.........................................................1 Digital 1600 (1)
.........................................................2 Digital 1600 (2)
.........................................................3 Drop Amp and SBEs, including analog halves of the 1600s
.........................................................4 Capped

So with current-ish drivers you ought to be able to get whatever your local Comcast is delivering on QAM 256 (just the locals, local HDs, and some assorted junk) directly off the cable.

Some of the early 1600 cards could not do QAM, just 8VSB for OTA channels. Their serial numbers (74031 and 74551) are listed on the 1600 Wiki page at linuxtv.org : [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)

Some editions of mythtv have scanning difficulties with the 1600; for these a command-line dvb utility like "scan" can be used to generate a channels.conf file that you can load in mythtv's backend setup.

Even when digital scanning is working perfectly, signal strength will always read 0%. The card should still get locks and be able to tune anything unencrypted that's out there on QAM 256 (or QAM 64). Most of these are likely to be clustered in the ch. 60s, 70s, or 80s as the scanning process chugs along.

---

### Post by CaptainPatent on 2010-11-30
Thanks to the above two posts I have verified in linux that the digital side is functional.

I hadn't looked at the Wiki for the Hauppauge 1600 in quite a while so the digital setup portion was new and I'm glad it was there.

The non-working channels for me aren't on the digital side, they're actually on the analog side and no amount of tinkering / updating them over the past couple of years has fixed them. I'm 99.9% sure those particular channels are blown out or malfunctioning on the tuner card itself.

My only remaning question is:
Is there a good way to correlate the digital side of the tuner card to a schedules direct account short of manually entering all of the information?

---

### Post by the_pod on 2010-11-30
I have this card.  FWIW, I think if you do a V4L-DVB update you'll get better signal / results. But it's my understanding that there are some issues with this currently so just keep that in the back of your mind.

Personally, I map them by hand tabbing back and forth b/w SchedulesDirect & the MythWeb channel interface.  You can look into scte65scan for a fancier solution that does an auto-map to Comcast digital channels but I've not had much luck with that, personally. 

Throw in the fact that you'll probably be receiving both an HD and SD signal for at least the networks and you'll probably want to manually hide one of them from the tuners so that you can be assured of recording only from the HD channel.

Sounds like you're well on your way however.  Enjoy.

---

### Post by lnoland on 2010-12-01
> **the_pod said:**
> Throw in the fact that you'll probably be receiving both an HD and SD signal for at least the networks and you'll probably want to manually hide one of them from the tuners so that you can be assured of recording only from the HD channel.

That seems rather drastic.  You would rather miss a show than have to watch it in SD?  I just drop the priority on my analog channels so that the digital tuner is chosen if it's available and the analog serves as backup.

To the OP: I have this card and though the digital side consistently yields poorer performance than my HDHomeRun units in terms of the ability to lock in stations, it handles most of my stations OK.

As for the ability to correlate the stations to SchedulesDirect without doing it by hand, I seem to recall that there is is some sort of configuration file you can create that Myth will use but I don't remember where I read about it -- in the WIKI, I think.  I don't know how easy it is to generate.  You could probably convert the channel table from SchedulesDirect into text and parse it with a shell script or AWK, and generate the SQL necessary to update the tables in Myth but I don't know if it'd be worth it to avoid a one-time job of entering the channels by hand -- of course, while it probably should be a one-time job, I've had to do it several times due to problems, when adding tuners, etc. (maybe I should work on a script).

---

