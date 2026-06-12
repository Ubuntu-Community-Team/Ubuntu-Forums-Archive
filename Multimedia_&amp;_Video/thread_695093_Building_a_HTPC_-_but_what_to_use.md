---
title: "Building a HTPC - but what to use?"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by Svenstaro on 2008-02-12
Hey there,

first of all, I know there are other similar threads but they don't contain quite what I want or are pretty old. 

So:
As the title states I want to replace my current analog living room multimedia equipment with some kind of Linux HTPC. 
My choice of hardware doesn't really matter here I guess because it's all Linux compatible but I'm going to list it anyway:

CPU: Intel Q6600 
Mainboard: GigaByte GA-P35-DS4
Graphics card: XFX GF8500GT passiv OR XFX GF8800GT (yes I considered using it as a game console as well)
Harddrive: 500GB 7200RPM SATA2
RAM: 4x1GB 800mhz OCZ
Card reader
DVB-T: Hauppauge WinTV NOVA-T Stick
Analog TV: Some old Hauppauge which I have lying around
I want to use a Gyromouse and a wireless keyboard.


Now let's look at what I want it do:
- Watch and capture TV, simultaneously + Timeshift and scheduled recording times 
- Automatically fetched program catalogs (for German TV)
- Play games
- Fetch and play various multimedia (all kinds of sound and video formats which sometimes use subtitles) from anywhere on the network (though only where specified), download Album covers and other metadata if possible, maybe show some visualization while playing 
- View/Edit/Store high quality pictures (most likely Gimp will do the job here)
- Play DVDs
- Show RSS feeds when idle


Doesn't look so hard up to now, does it? I know there are many distro's and programs available for individual parts of what I want to do but sadly none seems to be able to accomplish doing it all and properly!

Even with 3 years of allround Linux experience I fail to pick a bunch of software from the pool that does what I want because I want a frontend which contains basically all of the playback functionality in order to be able to watch/listen/look at media in an easy fashion but I also want to be able to gain full control of the system like I would with any Ubuntu Desktop whenever I need to. For example editing photos would be one such case.

What Mythbuntu does seems nice but last time I tried it wasn't stable nor contained any German program guide. Now I don't mind hacking a few scripts here and there but I at least want a good base to expand from. I also wouldn't mind a complicated MythTV installation if it would just work afterwards :).
Elisa does seem really nice indeed, sadly it doesn't do TV and I'd like TV to be integrated in the frontend.

My output/input structure would look like this: Analog/DVB-T card receive signal -> software recodes it -> graphics card outputs it to the LCD-TV using S-Video  - would it work like this?

So what do I choose? Please help me :)

Thanks, 

Sven

---

### Post by Svenstaro on 2008-02-13
*bumpy*

---

### Post by theacoustician on 2008-02-13
It Myth doesn't do it for you, I doubt you're going to find what you want on a Linux platform.  I start with installing the latest version, then hacking your way towards satisfaction.  If you post questions in the Mythbuntu subforum here, the devs will see it and hopefully answer you.

That system is a little on the overkill side for a HTPC, so no real worries there.  The only thing I'd look up is the compatibility of that DVB stick.  I know that some of the USB sticks are a bit of a pain on the ATSC/QAM side, but I know little about their DVB counterparts.

The big question is why would you want to hook your HTPC up to an LCD using s-video?  Use VGA or DVI.  You'll get a much better picture.  If you're planning on watching HD content, that's not even possible over s-video.

---

### Post by Svenstaro on 2008-02-13
Thanks for the answer,

if I knew LCD-TVs had DVI input I wouldn't even have thought about using S-Video.
The DVB stick is well supported by Linux.

So you're saying go for Mythbuntu? I'll try it then though there will be a lot of hacking involved :)

Still open for other suggestions though.

---

### Post by theacoustician on 2008-02-13
> **Svenstaro said:**
> Thanks for the answer,

if I knew LCD-TVs had DVI input I wouldn't even have thought about using S-Video.
The DVB stick is well supported by Linux.

So you're saying go for Mythbuntu? I'll try it then though there will be a lot of hacking involved :)

Still open for other suggestions though.

Well, that's where I'd start.  That or KnoppMyth.  Those are truly the easiest installs out there.

For Mythbuntu questions : [http://ubuntuforums.org/forumdisplay.php?f=301](http://ubuntuforums.org/forumdisplay.php?f=301) .  I'm sure there are more than a few people there who will help you hack your way to happiness.

---

### Post by peterthewolf on 2008-02-13
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

Try Myth again using standard gutsy and the above guide.

---

### Post by Svenstaro on 2008-02-14
Thanks for the help guys, I'll start off using Mythbuntu as a base and will then hack my way towards my goal.

---

### Post by chayzer on 2008-02-28
If they finish the port of Xbox Media Center to Linux, it may be an interesting option for media playback over the network, ripping and such. I've been using an Xbox as an HTPC for years, and just built an htpc, as the Xbox is on the brink of not being able to handle todays HD content. If they had a decent Myth plugin for it, I'd be really excited for XBMC Linux. Until then, I might have to get into the Mythbuntu thing.

---

### Post by steefjeqv on 2008-02-28
Hi,

I've noticed you're living in Germany.

You may want to check out VDR. It has a huge German (and European) fanbase.

[http://www.vdr-portal.de/board/portal.php]("http://www.vdr-portal.de/board/portal.php")

[http://www.vdr-wiki.de/wiki/index.php/Hauptseite]("http://www.vdr-wiki.de/wiki/index.php/Hauptseite")


Greetings,
Steven

---

### Post by Svenstaro on 2008-02-28
Wow nice,

looks like it's really popular here, I'll try out both Mythbuntu and VDR!

---

