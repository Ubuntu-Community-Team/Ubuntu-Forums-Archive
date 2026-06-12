---
title: "Is a Hotel setup possible"
date: 2010-07-16
forum: Mythbuntu
---

### Post by chipppy on 2010-07-16
Good Evening

I am looking at building a setup with the following using high end commercial sever system and domestic thin clients

12 tuners
1 server BE only
NAS 10TB or more
47 thin clients

The purpose is to provide TV with program time shift capabilities to a 47 room mining camp.  Later looking at utilising some of the other Mythtv features

Is this possible via a mythbuntu 10.04 install?
Has anyone every heard of a system this big???
Any advice?

Cheers
chipppy

---

### Post by LowSky on 2010-07-16
Sounds like a huge very but possible project.

---

### Post by ian dobson on 2010-07-16
Hi,

12 tuners, what sort of tuners do you want to use? If you're thinking about USB then take into consideration that USB has limited bandwidth. So you'll need to make sure that each tuner is on it's own HUB (even if it's on the motherboard). 

Or you use PCI tuners and add one master backend server and several slaves. This could actually be a better solution as you'll have some redundancy in the system.

Sounds like a really interesting project. Abit larger than my currect system (4 Tuners, Quad Core,8Gb ram, 12Tb disk).

Regards
Ian Dobson

---

### Post by LowSky on 2010-07-16
12TB? That is a lot of space!

I'm getting by on 1.25TB, 3 Tuners, 4GB of RAM, and a Quad core AMD Phenom, and I feel its more than enough.

Just a thought but network traffic might be a bottleneck too. 47 clients maybe running all at once seems like a very heavy load.

---

### Post by SnafuFlux on 2010-07-16
I'm surprised no one has questioned the 12 tuners.  if you're going to have 47 clients, you're going to want at least 47 tuners, no?  Each client can watch their own live television?

---

### Post by tgm4883 on 2010-07-16
> **SnafuFlux said:**
> I'm surprised no one has questioned the 12 tuners.  if you're going to have 47 clients, you're going to want at least 47 tuners, no?  Each client can watch their own live television?

Give me time, the thread has only been here 2 hours ;)

Though I would suggest more than 12 tuners, 47 is too many. There are many things to consider.

How many channels are they? If there are only 20 channels, why would he need 47 tuners?

Digital or analog? Are any of the channels on the same multiplex? If so, you should just need a single multirec capable tuner for that multiplex (maybe a few for load balancing)

You surely don't *need* to have a tuner for each room. You should be able to assume that not every room would want to watch Live TV at the same time. 

10 TB does sound like a lot, but I would assume he plans on recording and making available a lot of shows. Possibly videos/music as well. You need storage for that.

I would recommend multiple backends to help distribute the load.

---

### Post by chipppy on 2010-07-23
Good Afternoon

Thanks for all the feedback and questions.  some i didnt think of and I will need to work on them to see if things are going to be possible.

first this is not a true hotel, it is a mining camp for Fly-in-Fly-out personnel.  Nearly the same people in the same rooms when there are on site and there is two different crews that swap between home and camp.

To answer a few questions
**Tuners**
12 digital free-to-air channel (no pay tv channels)
12 PCI tuners via
6 fusionHDTV cards (2 tuners per card)
Looks as through the various Servers mobo looks like I may have to have two servers just to get the 6 slots physically (is possible with one)  This might be a good idea to allow for redundancy and also load sharing.

**Network**
Running a 1Gig network from server to thin client, including all switches.
there is currently a spare ethernet cable point in every room so no need to do any wiring just need to wire up each set of 6 rooms to a backbone
I dont know if band width will be an issue.  I dont understand networking very well but I am working on the assumption that if 5 clients are watching the same Tv show at the same time then the same 1 packet is sent to 5 different points at the same time eg it just gets copied when it splits off at different switches.  Not sure if this is true but I hope so.  

**Front Ends**
Will be basic thin clients munt on back of LCD screens, with Wii remots setups

**Storage**
The severs will have local RAID 1 for the OS (mythbuntu 10.04LTS)
Yes there is mass storage (NAS) to all for recording (time shift) of various TV shows.  Basic script to delte out recording more then a few months old (still working the detail) as most recordings will be sports recorded on weekend while blokes are at minesite onshift.

**Legals**
the company legal department is still working out what we could and cannot put into the system eg music, videos etc.  Personally I feel that if we can get TV shows and time shift recording then that is a huge improvment on our current camp life.

As to is it a big project.  ***YES*** oh my god it is the biggest thing i have ever done if I get the green light from the camp boss.  

hope this answers some of the questions.  Please keep the questions coming as i need al the help in preparing this as I can.  It is a scary prospect to set this up but I tyhink if I can get it all working then it would be a great showpiece for mythTV and the GNULinux communities in general.

Cheers 
chipppy

---

### Post by andree_b on 2010-07-23
> **chipppy said:**
> 
I dont know if band width will be an issue.  I dont understand networking very well but I am working on the assumption that if 5 clients are watching the same Tv show at the same time then the same 1 packet is sent to 5 different points at the same time eg it just gets copied when it splits off at different switches.  Not sure if this is true but I hope so.  
That would be multicast and i am pretty sure MythTV does not support this - so every FE will get it own copy.

You should take a look at the VideoLan project which basically did something similar: serving TV/video to an university campus via lan. They probably do have multicast functionality.

Simply streaming 12 channels via multicast to clients with timeshift-able player + upnp video server would be probably more viable than a mythtv setup which will have some massive scaling problem i think.

PS: if some of these digital channels are on the same multiplex you don't need 12 tuners

---

### Post by barberio on 2010-07-23
Since it's digital, do you know the local transmitter's MUX layout? With recent version of MythTV you only need one tuner per transmitter frequency used, and 'channels' are usually multiplexed onto the same frequency. The number of transmitter frequencies used can be quite a lot less than the number of logical TV 'channels'.

For instance, over here in the UK, we have six transmitter frequencies used for Freeview, so would only need six tuners to cover 50+ channels of TV and Radio.

MythTV's setup program will let you look up how many "transports" there are, which will list each of the frequencies in use. For full coverage, you only need one tuner for each.

(Note, some transports found by the setup scan may even be empty. Particularly if it's a cable service. And you won't need a tuner for them since there's nothing to see on them.)

---

### Post by uncle hammy on 2010-07-23
> **chipppy said:**
> I dont understand networking very well but I am working on the assumption that if 5 clients are watching the same Tv show at the same time then the same 1 packet is sent to 5 different points at the same time eg it just gets copied when it splits off at different switches.  Not sure if this is true but I hope so.
No, that will not happen.  

Think of it this way.  Unless all 5 clients were to start watching the same program, at exactly (and I mean exactly) the same time, they would have want different parts of the program at any given time.

---

### Post by chipppy on 2010-07-28
Good Afternoon

> Since it's digital, do you know the local transmitter's MUX layout? With recent version of MythTV you only need one tuner per transmitter frequency used, and 'channels' are usually multiplexed onto the same frequency. The number of transmitter frequencies used can be quite a lot less than the number of logical TV 'channels'.

I like the transports information.

We have only 6 transmitting stations but each station has multiple channels so in theroy there could only be 6 frequency with multile transports for each frequecny.  this would make life a lot easier.
do you know a good like for me to read through to get a much deeper understand of how this all works in Mythtv?> 

---

### Post by alien878 on 2010-07-29
The multirec functionality just worked for me in mythtv.  Just set the max tuners for the card in mythtv-setup.  Note that I just checked and for my card, max tuners can not be greater than 5.

(I no longer use this functionality.... I got annoyed at it because one of my transports has the HD and SD version of one channel on it and mythtv kept recording both versions)

---

### Post by newlinux on 2010-07-29
How much concurrent use of livetv and recordings do you expect?

---

### Post by tgm4883 on 2010-07-29
> **alien878 said:**
> The multirec functionality just worked for me in mythtv.  Just set the max tuners for the card in mythtv-setup.  Note that I just checked and for my card, max tuners can not be greater than 5.

(I no longer use this functionality.... I got annoyed at it because one of my transports has the HD and SD version of one channel on it and mythtv kept recording both versions)

Sounds like your schedule wasn't set up right or the channel data was different. Couldn't you just have deleted the SD channel?

---

### Post by alien878 on 2010-07-30
> **tgm4883 said:**
> Sounds like your schedule wasn't set up right or the channel data was different. Couldn't you just have deleted the SD channel?You're right, I could delete it.  However, it heavy rain/snow, the HD channel drops out before the SD, so I wanted to keep it.  I often use "any time on this channel" record and both channels are "the same" so it recorded both.  Match duplicates doesn't seem to work in this situation.  I could have probably used "one per day", but I would have to do that every time.  Setting maxrec to 1 was easier since I never use PIP.  It isn't very useful when it only works for the channels on the same transport.

---

### Post by nickrout on 2010-07-30
You really want to check out your local copyright law. This would be illegal in my country (NZ). Probably will be where you are too.

But from a technical point of view if you just want live tv I would be inclined to multicast using dvbstream. This will, as I say, only work for live stuff, but will essentially enable you to repeat a whole multiplex via multicast. Each client could then choose which selection of pids it wants to play.

---

### Post by chipppy on 2010-09-11
Good Evening

Sorry for the long break with working on this.  Work had me flying all over the place.  It was madness the last month or so.

Company legal says that live TV and time shift only allowed

---

### Post by tgm4883 on 2010-09-11
> **chipppy said:**
> Good Evening

Sorry for the long break with working on this.  Work had me flying all over the place.  It was madness the last month or so.

Company legal says that live TV and time shift only allowed

Recording would be considered time shift.

:EDIT:

Just not backing up to disk

---

### Post by chipppy on 2010-09-11
Good morning

As company legal explained to me (for Aussie only).
The recording (storage of any type) of TV content is illegal.  Time shift of TV content for the viewing at a later date is legal.

The time shift bit is very fuzzy though there is no definations for max time the shift can be (hours, days, months, years, etc)

The is no defination if the program that has been time shift can be watched more then once.  Eg we work 2 12 hour shifts at work so day shift and night shift want to watch the same program (footy grandfinal) then can the two shift use the same timeshift or do we need to have two time shifts of the same program?

the is no defination if the time shift program can be watched in multiple sitting or must it be played from start to finish no matter what.

And a few more wierd things like the above

So the end of it all is that I have to setup the following type setup.

All time shifts have to be autodeleted after 6 weeks from all and any storage devices(3 crew rotations).  If you record something this trip to work it is gone after your next trip at work. (not to hard to setup.

all personall are able to time shift and play programs.  (derrrrr that is what MythTV does anyway. 

There can be no access to remove time shift content from the storage devices (who wants to let people near the system to download to USB harddrives anyway).  I think simple password protect via user accounts should cover that.

Now the hard part of trying to prove this will work so that I can get the dollars from the company.


Big thanks to everyone for the help so far
Cheers
chipppy

---

