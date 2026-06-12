---
title: "Simple question about using two DVB cards"
date: 2008-01-15
forum: Mythbuntu
---

### Post by Glenhawk on 2008-01-15
Hi all,

***When installing a second DVB card do you need to add a second Video Source?***

*This is the root question of my testing at this stage but see below for a full description.*

**_Background_**
I have recently bought a second (seemingly) identical Ultraview (DVICO) lite DVB card and have installed it in my PC. 
I wasn't sure exactly how to set it up so all I did was open the backend settings, added a capture card (with unique ID) and another Input Connection. I wasn't sure if I needed an additional Video Source because the Listing Grabber and Channel Frequency Table would be the same... so I didn't add one.
I started up the front end and immediately I was able to record two things at once or watch one while the other was recording so I figured it had worked.

**_Problems_**
Since installing the second card sometimes recordings are glitchy/corrupted and I am not sure why and cannot identify which card was used to record them. I was thinking that maybe the second card needed to be tuned in separately, perhaps it needed a separate Video Source? 
Alternatively perhaps the cable connection between the first card and the second card is dodgy? (each card has a pass-through connector so the second card connects to the output of the first)

**_Testing_**
I have currently added a second Video Source and scanned for channels using the second card. I now have duplicate channels, one set for each card. I will now wait and see if the glitching/corruption problem remains.
I checked that I could still record two programs at the same time without conflicts and I could however in my upcoming recordings I noticed one strange conflict.
On one channel I am recording a few programs end-to-end and on another channel I have a (1/2 hour) recording scheduled to start halfway through one (hour) recording (on the other channel) and finish at the same time. Basically two recordings finishing at the same time as another recording begins. The half hour program is the conflict.
I tried fiddling with the capture card assignment for each program with varying results but always one conflict remained.
I have not hard-set any programs to over record but I have got soft-settings for over recording. This should not cause conflicts. I am thinking that maybe adding the second Video Source caused this but I hadn't noticed it before and did not have time to change the setting back before I left the house.
Any thoughts?

**_Solutions_**
*I will add solutions here as I figure them out*

---

### Post by ubnewbie2 on 2008-01-15
You should only have one video source, and both cards should use it.  The problem may be that the second card is seeing less signal, due to the passthrough.  There will be some loss as it passes through the card, and the second coax cable.  Keep the second cable as short as possible, and always use good quality cable. If that is not enough  you might consider buying a cheap amplifying splitter. This is what I have done, as I need to get good signal to my mythbox with 2 DVB cards (with passthrough) and also my flat panel. This will raise the signal level, and so, potenitally fix your problem.

One other possibility is, if your mythbox is a little underpowered, it might be struggling to record 2 shows at once, especially when watching another recording at the same time.  DVB cards provide a digital stream that is "easy" to record however, as it doesn't require any processing.  It is just streamed to the file on the disk, so even modest systems can usually cope.  Playback, however, can present problems, as the mythbox has to do a lot more work to display the picture.

---

### Post by Glenhawk on 2008-01-15
Thanks for your reply,
I will check on the cable issue. It is funny that it only happens on a few recordings (say 5%).
Sometimes it is only for half of the recording but it is always a constant interruption and not just a few glitches here and there. EG. I was watching a recorded episode of Futurama, a few minutes in it starts looking like a badly scratched DVD and this continues for about 10-20mins and then it is perfect again.

Regarding the system specs, don't worry it is a bit of a hot-rod (2.67GHz Dual Core Pentium, 1333FSB, 2GB DDRII, 512MB NVidia PCIe VGA) and I usually only playback on my remote frontend under the TV (P4 2.6GHz, 2GB DDR)

I'll look into it further and see what I uncover.

PS: is there anyway to identify which card was used to record a particular recording? If the glitches are always on the same card, that would be a nail in the coffin!

---

### Post by ubnewbie2 on 2008-01-16
Hmmm,   if the problem recordings are on some channels and not others, it can be due to borderline signal levels, because different channels are on different frequencies, and different frequencies suffer different amounts of signal loss, both during transmission to you, and also as your antena receives them and they travel through your cables to your equipment. Even the weather has an effect.  

For example: I had only one channel that played up, and then only if it was raining !  Boosting the signal fixed it.

As for finding out which card, if you look at mythtv's web based status page on mythweb on your server, you'll see, amongst other things, a list of upcoming recordings, and which encoder (which card) will be used.  Also the first column, on the "Upcoming recordings" page tells you which encoder will be used.

If it's like mine. it always uses encoder 1, then, if that is in use and another program needs to be recorded, it will use encoder 2.   I believe you can play around with priorities, but by default, this is how it works.

---

### Post by Glenhawk on 2008-01-16
I think I may have worked out the problem. I think I am on the edge of another broadcast area. I can occasionally pickup duplicate channels in the higher frequency bands. The problem is that they are often lower powered and because they are later in the table they OVERWRITE the good signals. 
I realised this when I removed the two Video Sources and went back to using one for both cards. When I retuned the channels and tried to watch TV, channel 10 was glitchy and I couldn't even lock on to channel 9. When I rescanned the channels I watched for the strongest signals. Luckily they were all at the bottom end so all I had to do was wait for SBS to lock in and then click cancel.
Time will tell but I think the problem is solved.
Thanks for your input. I will put some more info into this thread if I come across anything relevant.

---

