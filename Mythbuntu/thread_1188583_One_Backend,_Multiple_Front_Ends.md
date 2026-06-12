---
title: "One Backend, Multiple Front Ends"
date: 2009-06-15
forum: Mythbuntu
---

### Post by Mattaus on 2009-06-15
Bit of a mega-noob question here **but** what is the limitation on what 2 or more front ends can do with a MythTV front end hooked up to a single backend?

Can each user watch a different channel at the same time or are they limited to the same one? Would I require say 2 TV tuners to achieve this?

I'm reading through the MythTV docs section but thought I'd just post here first to get my foot in quickly ;)

Apologies if this is painfully obvious - I'm having a bit of a slow week lol

---

### Post by AboveTheLogic on 2009-06-15
I have 2 ATSC tuners on my backend. If I'm watching a channel on one of the front ends, then it's using one of the tuners. I can watch another channel on another front end and it will take up both tuners.

Then, if there is a recording coming up, it will prompt the front end using the tuner that the recording is set to use, asking if it will give up its channel for the recording.

I believe that if you are using a DVB-S tuner then you can watch more than one channel at once as long as they are on the same transponder, but I'm not 100% sure.

---

### Post by Mattaus on 2009-06-15
I am using a Leadtek DTV 2000H Rev.J card and I've only had it for 2 days (and its not fully setup yet) so I have no idea if it is DVB-S or not. I'll go googling.

I have a feeling I can watch multiple channels however as it has "Picture in Picture" stamped all over the box (from memory)

---

### Post by AboveTheLogic on 2009-06-15
looks like its DVB-T:

[http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=252](http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=252)

I'm not sure how that works honestly, I don't get DVB-T here in the States.

FYI:
DVB-S = Satellite
DVB-T = Terrestrial
DVB-C = Cable

ATSC = Digital Terrestrial
NTSC = Analog Cable / Terrestrial (recently mostly shut down in the USA)
QAM = Digital Cable

---

### Post by Mattaus on 2009-06-16
You're in Vegas...me and 5 mates were supposed to do a massive cross country trip starting in L.A and ending in N.Y in August this year but that fell through - absolutely gutted. Now I'll just be stuck in Australia lol.

Back on Topic..I'm not entirely sure what DVB-Anything means but I will go research it a bit and see what I can dig up. It's not overly important at the moment as I was asking from a "future upgrades" perspective, which is a long way off at this stage.

---

### Post by ian dobson on 2009-06-16
Hi,

Have a look here [http://www.overclockers.com.au/wiki/MythTV](http://www.overclockers.com.au/wiki/MythTV) there's alot of AU specific MythTV information.

Regards
Ian Dobson

---

### Post by Mattaus on 2009-06-16
> **ian dobson said:**
> Hi,

Have a look here [http://www.overclockers.com.au/wiki/MythTV](http://www.overclockers.com.au/wiki/MythTV) there's alot of AU specific MythTV information.

Regards
Ian Dobson

Cool beans - on my way now. Thanks.

---

### Post by AboveTheLogic on 2009-06-16
> **Mattaus said:**
> You're in Vegas...me and 5 mates were supposed to do a massive cross country trip starting in L.A and ending in N.Y in August this year but that fell through - absolutely gutted. Now I'll just be stuck in Australia lol.

[offtopic]
there is quite an Australia presence here, I really had no idea until I went to watch the AFL grand final at a local pub, I was asked quite a few times what part of Australia I was from, and I DO NOT look like an Aussie :)
[/offtopic]

DVB T/S/C, etc... isn't all that important to know about, but it does help to specify what kind of tuner you have when you are asking for help

I'm pretty sure that there is no ATSC/NTSC/QAM in AUS, but posting in a forums that have mostly USA users, the assumption might be made that you have one of those...

---

### Post by Mattaus on 2009-06-16
> 
DVB T/S/C, etc... isn't all that important to know about, but it does help to specify what kind of tuner you have when you are asking for help

I'm pretty sure that there is no ATSC/NTSC/QAM in AUS, but posting in a forums that have mostly USA users, the assumption might be made that you have one of those...

Yeah I didn't think about specifying that information before. The link that Ian Dobson provided in his post seems pretty helpful, though absic functionality of MythTV seems pretty uniform around the world. I think so long as I specify the right region ins et up I should be right, and eventually I will find out if I can have multiple users watching different content one way or another!

Oh, and AFL is for the southerners of our fine land. It's too frustrating a sport for me so I'm a Rugby League fan. More biff and more straight forward lol :D

---

### Post by AboveTheLogic on 2009-06-16
Yeah I worked with a lot of folks from Melbourne, they were huge fans.

Yes, you'll find out eventually. What I'm wondering is if DVB-T works like DVB-S in that there are more than one stations available per frequency (transponder or transport), allowing the tuning of multiple stations from the same transponder. If there are shared frequencies with DVB-T, you may benefit from the same effect.

---

### Post by Mattaus on 2009-06-16
The wiki page on DVB-T is spanglish to me unfortunately.

---

### Post by ian dobson on 2009-06-16
Hi,

OK I'll try and explain. DVB stands for Digital Video Broadcast. There are 4 DVB standards (DVB-c,DVB-s,DVB-t and DVB-h)

DVB-C Digital signal over Cable (Has the highest transfer rates due to direct cable connection)
DVB-T Digital signal over normal terestrial transmitter (Lower transfer rates than DVB-C but you only nee a simple antenna)
DVB-S Digial signal over a satelite (More bandwith than DVB-T but you need a special antenna (Dish) to get a signal)
DVB-H Like DVB-T but for handheld devices (Low bandwidth, low resolution pictures)

The DVB system uses the same basic transfer system as Analoge TV but with two big differences, and they are:-
1) The data is send as a digital signal rather than analoge. Which means the pictures can be compressed, error correction added, extra signals can be included (Multipe lnguages)
2) As the data is being compressed, DVB can transmit several different channels together in the same space as a single Analog chanel would use.

For example about 6 months ago by TV provider stopped sending one channel through Analoge and went over to Digital and I got 4 new channels.

I hope this helps abit
Regards
Ian Dobson

sorry if the spelling is abit off, I don't use by English that often and it's been a long day (13hours in the office).

---

### Post by Mattaus on 2009-06-16
Hey that was a very good explanation, much appreciated. I got MythTV working last night but am now having playback issues (bad stuttering and double image) but I have already posted about that in a new thread.

---

### Post by laffinet on 2009-06-16
Generally speaking you can watch one channel with each tuner card.

However...
as someone already said, with DVB-T you can watch two channels with one card if both channels are on the same multiplex (whatever that means).
To do this you have to change a setting in mythbackend setup (under the capture card I think). There's a section there somewhere that says "available tuners" or so. Change that and you're set to watch 2 channels.

---

### Post by Mattaus on 2009-06-16
> **laffinet said:**
> Generally speaking you can watch one channel with each tuner card.

However...
as someone already said, with DVB-T you can watch two channels with one card if both channels are on the same multiplex (whatever that means).
To do this you have to change a setting in mythbackend setup (under the capture card I think). There's a section there somewhere that says "available tuners" or so. Change that and you're set to watch 2 channels.

Sweet - once I manage to solve some of my other problems I might look into it. I think I'm in over my head at the moment lol.

---

### Post by AboveTheLogic on 2009-06-16
> **laffinet said:**
> multiplex (whatever that means)

that just means that more than one channel is 'multiplexed' onto the same frequency

that's how DVB-S is

with my DVB-S card, it just worked like that, I could be recording one thing and when I went into the guide, the other channels on the same frequency (transponder) were selectable, the rest were greyed out (except for the channels that were associated with my ATSC tuners)

---

### Post by laffinet on 2009-06-16
> **AboveTheLogic said:**
>  I could be recording one thing and when I went into the guide, the other channels on the same frequency (transponder) were selectable, the rest were greyed out

That's how it works for me, too, but I had to change the setup in mythbackend setup, as mentioned above. Don't know why it didn't work out of the box.

---

