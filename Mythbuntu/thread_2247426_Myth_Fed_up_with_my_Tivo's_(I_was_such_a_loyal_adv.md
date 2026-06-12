---
title: "Myth: Fed up with my Tivo's (I was such a loyal advocate 'em too)"
date: 2014-10-07
forum: Mythbuntu
---

### Post by david144 on 2014-10-07
Hi all,


I'm fed up with my TivoHD units constantly crashing and rebooting and missing parts of shows, so I've decided to invest some money in building some MythTV boxes and I was wondering several things. 


I'm new to Myth.. very very new, and I've glanced at the information available but there is a lot. The wiki is HUGE, there are tons of different forum posts all over the place, many of which are out of date information for old releases and quite frankly I just want some basic confirmation that will help me decide to embark on this project.


To start I'm considering using the Silicondust HDHomeRun DUAL 4thGen tuners because I want to use a virtual machine as the backend. The product home page says it will just show up as a tuner to select from, I'm assuming UPnP goodness :)

 I'm guessing there's no point to installing multiple virtual backends on the same ESXi host unless I wanted some kind of redundancy for upgrade testing (but that's what snapshots are for imho ;) hehe)

Lastly I am using an NFS export for storage, although I could use a 4TB or 2TB direct attached storage vmfs volume for speed, but I'm hoping there's a way to move the content off to my NFS storage automatically and still access it via the frontends. (I'm guessing this is the Migrating to Storage Groups section on the wiki so I'll need to bone up on the wiki some more) 


1. Can the Myth backend access multiple HDHomeRun-Dual units? 
The wiki makes it sound like it: 
> You can have multiple servers (called "backends"), each with multiple capture cards in them. All scheduling is performed by the Master backend, which arbitrates which recording will be performed by each device. All recording requests are managed by the Master backend, so you can schedule a recording from any client.
    my picture below depicts 4, for a total of 8 tuners, and no I wouldn't be recording 8 channels at once but I would like to be able to record 2 or 3 at once and possibly watch 2 others (one in the bedroom and one in the living room)


2. Is it possible to have multiple frontends accessing a single backend? (I'm assuming yes because it would be the Master backend) Again the wiki appears to portray this but I want to be absolutely sure that I don't need to build a bunch of backends just to support multiple frontends. (Call me lazy for I am, but aren't a lot of us? ;) hehe)


3. Can the frontends, also access the HDHomeRun-DUAL tuner's directly or is that only done via the Backend? (maybe I answered my own question with the end of the question but I'm hoping to get confirmation)

Here's my general design thoughts:
[ATTACH=CONFIG]257027[/ATTACH] 

I have 4Gb/s LAG trunked between the switches but the ESXi host server NICs are not teamed because I had trouble getting ESXi and my Switch to play nice so I just went back to all active's using Route based on the originating port ID. This would mean I only have a single 1Gb connection to the backend. This was where I thought I might have a case for some slave backends so the traffic got split up some but I honestly haven't decided to go for multiple HDHomeRun-DUAL's yet until after I made this post and get some responses. I'm hoping this reaches some people who have multiple HDHomerun devices connected to their backend and to see if they have any advice or experience with bandwidth issues.

Thanks for taking your time to read my post :)

**[COLOR=#ff0000]*-*-*-*-*-*-*-*-*-Some irrelevant info below-*-*-*-*-*-*-*-*-*-*[/COLOR]**
If you're wondering, my Storage Server build can be found [here]("http://ubuntuforums.org/showthread.php?t=2220677") I've enabled NFS since the time of writing, and also had one drive of my md0 fail so I'm going to be updating the case for hotswap bays and adding some hot spare standbys. 

Sadly though I need to ditch my custom cabinet I built with my cousin:
[ATTACH=CONFIG]257030[/ATTACH]

It won't fit the new case I'm buying :(

and..

The addition of the storage server and my L3 switch in the bottom of the cabinet pushes the heat dissipation ability of the cabinet to it's limit for my comfort. (Saw a reading of 46degC the other day off the SAN server while in the cabinet with the A/C running, it can pull 52-C outside the cabinet in my office with only the open air, and I have measures in place to shutdown automatically at 56.1-C)

 The last thing I want to do is add more drives (ipso facto more heat) and have my closet catch on fire because I didn't plan enough CFM into "*The Beast's cave*"... well.. that and I'd like to get some closet space back ;) ROFL

---

