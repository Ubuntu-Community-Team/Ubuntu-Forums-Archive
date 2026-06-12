---
title: "Missing channels on Hauppauge 2250"
date: 2012-08-30
forum: Mythbuntu
---

### Post by Lance Mountain on 2012-08-30
I created a new thread for this from my previous one [here]("http://ubuntuforums.org/showthread.php?t=2049399")

Basically I would tune to some channels and get a buffer error but I resolved that and then realized Iw as not getting channels like ESPN, Bravo, Fox Sports etc..

So this leads me to believe I either do not have the Hauppauge setup properly or I am not supposed to get certain channels. 

If I look at SiliconDust site and change the provider to the first Cox Cable choice, I see all the channels I actually am getting properly via the Hauppage 2250. So are these the only channels I should get?

I am confused because if I hook a tv with a ClearQAM tuner directly to the cable I will get more channels like ESPN, Bravo, Fox Sports. These other channels are also listed in Schedules Direct lineup for Cox Cable (basic) not even digital cable.

So have I setup my 2250 wrong so that it's not picking up these other cable channels? Or is that a limitation of this tuner card? I have connected the tuner directly to the cable too, just to eliminate any splitters causing issues, no difference. I used [this post]("http://ubuntuforums.org/showpost.php?p=11205874&postcount=425") by LowSky to set up my card.

---

### Post by Lance Mountain on 2012-09-01
Ok so now I am closer to a solution. I put the tuner card in my win7 box and it worked fine, media center found all the channels I expected and even had them in the right order with the right IDs & automatic program data, so why am I using mythtv?

I'm down the mythtv road now and I don't want it to defeat me. In media center I checked the properties of the channels I wasn't getting with MythTV and noticed they were analog.

So now I search around and find out mythtv had problems with analog in .23 is that still true with .25? If not do I have to setup a separate capture card to get analog channels, ie mpeg2 capture card vs DVB? because both show as options for my Hauppauge. But when I setup the mpeg2 card and then attach an input connection the channel scan finds nothing.

---

### Post by nickrout on 2012-09-01
> **Lance Mountain said:**
> Ok so now I am closer to a solution. I put the tuner card in my win7 box and it worked fine, media center found all the channels I expected and even had them in the right order with the right IDs & automatic program data, so why am I using mythtv?

I'm down the mythtv road now and I don't want it to defeat me. In media center I checked the properties of the channels I wasn't getting with MythTV and noticed they were analog.

So now I search around and find out mythtv had problems with analog in .23 is that still true with .25? If not do I have to setup a separate capture card to get analog channels, ie mpeg2 capture card vs DVB? because both show as options for my Hauppauge. But when I setup the mpeg2 card and then attach an input connection the channel scan finds nothing.

Well if you had told us they were analogue channels the answer may have been more obvious.

I don't think you need to scan for analogue, you get the channel details from schedules direct. At least I think so, I don't use analogue at all.

PS I think that means you need 2 lineups on SD - one digital and one analogue.

---

