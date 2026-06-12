---
title: "Analog v Digital signals"
date: 2008-03-28
forum: Mythbuntu
---

### Post by dsbw on 2008-03-28
I've gotten as far as using the DVB-Util "scan" to detect channels on my Kworld ATSC 115. When I tried capturing, I got a noisy picture once and then error messages.

I've tried subsequently to scan inside of MythTV with no luck. Now, from the channels.conf, I know that I hit 8VSB frequencies--and I would've thought broadcast would be the right place to look for those, but no dice. (I've now run through the various "cable" ranges. I tried importing channels.conf but got a parse error. Got the same error at the command line when trying to tune a channel.)

Another thing I did was run tvtime. This ended up confusing me. It picked up channels but they were pretty clearly analog. (I think tvtime doesn't do digital.) But I didn't think I had anything set up for analog, and I know it's a big deal to set up the card for both. 

So, now, my questions:

1. An aerial's an aerial for the purposes of this discussion, right? I know you can buy specialized aerials, but old-fashioned rabbit ears will work for digital just as they do for analog (because the tuner's the thing, right?).

2. Traditionally, a cable sent an analog signal. But if you have digital cable, you get a digital signal. But the porcinophiliacs at the cable company don't want you to be able to capture that, so the coax coming *out* of the cable box is analog. Right?

3. This means mythTV boxen still probably want an analog capture device even when the analog broadcast signals stop, if capturing cable signals is desired. Otherwise, you're stuck with whatever they give you through the other ports.

4. I know that it's generally considered to be a bad idea to run an analog signal through a Kworld but with today's fast CPUs, is it really a big deal? (I ask because it didn't seem to strain anything to display the analog picture through tvtime.)

I'm going to put the troubleshooting question in a different thread, but I think these questions have a lot of general applicability.

---

### Post by volkswagner on 2008-03-28
> **dsbw said:**
> I've gotten as far as using the DVB-Util "scan" to detect channels on my Kworld ATSC 115. When I tried capturing, I got a noisy picture once and then error messages.

I've tried subsequently to scan inside of MythTV with no luck. Now, from the channels.conf, I know that I hit 8VSB frequencies--and I would've thought broadcast would be the right place to look for those, but no dice. (I've now run through the various "cable" ranges. I tried importing channels.conf but got a parse error. Got the same error at the command line when trying to tune a channel.)

Another thing I did was run tvtime. This ended up confusing me. It picked up channels but they were pretty clearly analog. (I think tvtime doesn't do digital.) But I didn't think I had anything set up for analog, and I know it's a big deal to set up the card for both. 

So, now, my questions:

1. An aerial's an aerial for the purposes of this discussion, right? I know you can buy specialized aerials, but old-fashioned rabbit ears will work for digital just as they do for analog (because the tuner's the thing, right?).

2. Traditionally, a cable sent an analog signal. But if you have digital cable, you get a digital signal. But the porcinophiliacs at the cable company don't want you to be able to capture that, so the coax coming *out* of the cable box is analog. Right?

3. This means mythTV boxen still probably want an analog capture device even when the analog broadcast signals stop, if capturing cable signals is desired. Otherwise, you're stuck with whatever they give you through the other ports.

4. I know that it's generally considered to be a bad idea to run an analog signal through a Kworld but with today's fast CPUs, is it really a big deal? (I ask because it didn't seem to strain anything to display the analog picture through tvtime.)

I'm going to put the troubleshooting question in a different thread, but I think these questions have a lot of general applicability.

[LIST=1]
[*]In theory you are correct.  An HDTV antenna is designed especially to pick up OTA HD.  An outdoor/attic mount should perform better than an indoor unit.
[*]Traditionally we only received analog via cable.  Currently my cable co. Time Warner sends digital cable(requires thier set top box to descramble and convert the signal for tv).  It sends standard analog for cable ready tv's, and analog tuners.   It also sends QAM digital signal for QAM capable tuners (kworld 110/115).  I currently recieve sereral HD channels this way (QAM).  Most of which would be avialable OTA if I had the proper antenna and was not alongside a mountain.  It also had a data frequency for high speed internet when connected to a cable modem.  Gee I wonder what else is on that coax?
[*]It certainly is required to capture channels with an analog tuner for protected channels, HBO, TMC, many other non basic cable channels. I don't think the cable co.'s are gonna flat out drop the analog signal if a large customer base has not subscribed to a digital plan.  Currently I can capture many unprotected channels in HD and SD via Firewire from my digital cable box(no tuner needed in Mythbox).
[*]If your pc can handle it no problem.  You will run into perfomance issues if you had several software tuners, or were running several frontends and commercial flagging etc.
[/LIST]

---

### Post by rickyble on 2008-03-28
*1. An aerial's an aerial for the purposes of this discussion, right? I know you can buy specialized aerials, but old-fashioned rabbit ears will work for digital just as they do for analog (because the tuner's the thing, right?).*

Just for clarification there is no such thing as a "specialized Digital antenna".  Digital signals from the tv stations are being broadcast on UHF for the most part.  The stations were all given a second frequency to use temp for digital.  They must give up one by 2009 and complete their move to digital.  To pick this up you still just need a regular old vhf/uhf antenna.  There is nothing special about them.  Of course the better your antenna and gain the better the signal and the better the distance.  I dont know about other places but here in NC most of the stations have chosen to stick with the new UHF assigned frequencies and plan to drop their old VHF but keep there station call numbers.  Dont let someone suck you into a HDTV antenna.

---

### Post by dsbw on 2008-03-28
Much appreciated, guys.

I find certain concepts slippery when there are other interests out there promoting false ideas. 

I've seen specialized digital antennae, for example, that imply you need them to get the digital signal. 

The cable companies keep talking up the change to digital, even though whether or not it affects their customers is entirely up to them. (This one I think is going to backfire.)

OK, cool. Now to figure out why I can scan all these swell channels on my $8 indoor rabbit ears *outside* of Myth but not *inside*.

---

