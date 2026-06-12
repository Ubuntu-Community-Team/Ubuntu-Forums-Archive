---
title: "Frustration: signal strength issues that move from channel to channel"
date: 2009-11-03
forum: Mythbuntu
---

### Post by jimbob91 on 2009-11-03
Here's the current hardware:

Intel E2180, 2gig DDR2, 500 gig system and recording drive, 1TB drive for videos
1 Air2PC tuner and 1 ATI HDTV tuner.

The system is about 1.5 yrs old, started at 7.10, now 8.10 with 0.21+fixes+Avenard repos.

I'm using a roof antenna, and a powered signal splitter, though I'm only 10-12 miles from the transmitters.  

From day one with this system, I've always had signal strength issues on one or more channels.  Though 85-90% of the channels come from towers about 10-12 miles away, I had iffy signal strength on a couple of them, mainly NBC and PBS channels.  Initially, I had 2 air2pc tuners, but eventually added the ATI tuner to try and combat this issue.  Both tuners always have the same issue on the same channels.  At times, I have had the PBS channels come in fine, then go back to weak signal strength, seemingly with no ryhme or reason.  

Last June, I thought that the digital TV transition would change things, because the frequencies would change.  That's exactly what happened.  After the transition, suddenly NBC came in at full strength and has been solid since.  And the PBS stations were solid for a short time, then went back to iffy strength, mostly unwatchable because they would "error displaying video" eventually.  However, I basically lost another station that had been previously solid, but I didn't watch that one so there was no impetus to fix the problem.

The latest issue cropped up last Thursday night.  I was recording back-to-back shows, Flash forward and Greys.  Flash forward was fine, Greys was skipping, popping, etc.  Now that ABC channel, which has been solid 99% since I've had the system, now has 8-10% signal strength on the air2pc tuner, and the ATI tuner is 50ish%.  And, my PBS channels which were 50ish%, now are solid.  All my other channels are fine, currently.

I did some testing on Saturday to see if it was antenna related.  I removed the powered splitter, and connected the roof antenna directly to one of the tuners = same result as above.  Then, I connect a short wire (1ft 6 in) to the input on the powered splitter, removing the roof antenna as an issue = same result.  

My guess based on those two tests, and the problem channel(s) move around on me, makes me think it is a software or DB issue.  

Sorry, this is getting long, but wanted to include as much relevant information as possible.

Mythbackend or Frontend logs don't show much, other than to indicate that the Preview won't work because the file size is zero (when signal strength is 8-10%).  I can upload them, if that would be helpful.

Any ideas on why I have migrating signal strength issues?

---

### Post by jimbob91 on 2009-11-03
A bit of new information.  I was just perusing some DTV transition sites and found one about my local market.  The 2 channels I was having problems with initially, PBS and NBC were at digital channels 34 and 35 respectively.  Since the transition last June, NBC moved to it's original VHF channel, and ABC moved from 50 to 35 (same as NBC used to be).  Could it be that I have some sort of interference going on, since the channels are directly adjacent to each other?  It would probably be obvious they were interfering with each other in the analog world.

---

### Post by iitywygms on 2009-11-03
I also receive my tv ota.
Don't feel alone with your reception issues.  I also have some channels that drop out one day and are strong the next.  Its just the nature of ota signal.
I seriously doubt this is an issue with mythtv or software in general.
I would hop on a forum dedicated to receiving tv ota and try to get some help there.  AVS forum maybe??  Thats where I got all my help.
good luck.

---

### Post by jimbob91 on 2009-11-03
Thanks, after finding out the information that they were adjacent channels, I am leaning that way as well.

---

### Post by jimbob91 on 2009-11-09
Well, after doing some research into OTA reception, I still wasn't sure what I was dealing with.  So, I bought a USB tuner so I could do some sanity checks.  I plugged the tuner into a Windows XP system to remove the Mythbuntu component.  

On my Windows PC, I connected the USB tuner (Hauppage 950Q), to my aerial antenna.  It had the same problems reliably tuning the 2 channels (34 and 35) that have been giving me trouble.  So, I was pretty sure it wasn't the tuner at this point, but I still did more tests.

Next I connected the little telescoping antenna that came with the tuner to the Windows and USB tuner config.  That gave me those 2 channels pretty reliably.  A few others had problems, however that wasn't too surprising.  So, I'm thinking my antenna is the culprit, almost every other channel comes in at 99% signal strength, so I'm thinking what gives?  And those channels come from the same set of towers, etc.

Anyway, next test was to cable my powered distributor/splitter into the mix.  So, connected the little telescoping antenna into the IN of the powered splitter, and one of the outs to the Windows PC.  Same results as above, I am reliably tuning the two channels in question.

Next test was with the Mythbuntu system and the small antenna.  Again, same good results on those channels.  A bit lower signal strength on the older tuners, but that was expected as well.

So, my thoughts are rolling to my aerial antenna.  When I connected it, I had to rewire it a bit as the original 300 ohm twin-lead stuff had rusted/rotted off and was long gone.  So, what I had one was just run a pair of wires from the antenna down the short mast to base, and then connected them to the 300 ohm to 75 ohm balun, and then ran coax from there.  Duh, I never thought that it would be a problem to do that, after all it was originally 300ohm twin lead that was unshielded, etc.  So, the theory was that the leaves had been shielding my un-shielded antenna wire, and when they dropped, the wire was causing too much interference by receiving the channel 34 & 35 signals as well.  On a whim, I wrapped that wire in some tinfoil, doing the best I could, but knowing it wasn't a solution, but wanting to verify that was the problem.  Bingo!  My signal strength shot up from 8-10% on channel 35 to 70-80.  It was still choppy, so I hadn't eliminated the problem, but it was enough to tell me that was the culprit.

So, this weekend I added a short length of coax up the mast of the antenna, connected one lead of the balun directly to the antenna, and had to run a short 5-6inch run to the other connection on the antenna.  A quick test reveals both channels, 34 and 35 coming in at 98-99% with no problems of note.  All my other channels are coming in strong as well, and I increased the strength on a lower power station that just went digital recently.

Maybe all this information will be of some use, to someone.  I'm glad I got it figured out, and it ended up being an easy fix.  I wished I had taken the time to figure out how to rewire the antenna in the first place.  It sure would have saved me some headaches and WAF.

---

