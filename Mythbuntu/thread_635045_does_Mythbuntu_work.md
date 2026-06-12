---
title: "does Mythbuntu work?"
date: 2007-12-08
forum: Mythbuntu
---

### Post by sturmey on 2007-12-08
I've spent three years off and on trying to get linux and my satellite TV card to work. I've read almost every how to that exists, and there isn't very many of them. so here it goes...

I have a dell server, I can boot off mythbuntu, and install it to the HDD. I have a twinhan 1020a DVB-s card as an input source.

-I'm pointing the satellite dish at G10r this is not DN or BEV shouldn't need any decryption. I'd like to be able to do that, but apparently you have to use Gentoo and spend a week compiling to do that.

when I went into the myth setup, I didn't have any sources. - read a bunch of confusing stuff, finally tried **apt-get install dvb-utils** and commenting out the wacom crap in xorg.conf (crashed the first time, why?)

after wasting another day, I finally killed all myth processes, and installed Kaffeine, it recognized the dvb card and allowed me to scan in some channels. (this is the first time I've seen linux acctually work with my card!)

tried to put the same settings into myth, doesn't show it locking onto the satellite.

So after all that, is there a walk through/ how to guide that you mother could follow that includes all the steps to get a satellite card to work with Myth that doesn't require a week of patching and recompiling?

Sturmey

---

### Post by barney_1 on 2007-12-09
I would be inclined to think you have your tuner set to scan for the wrong frequencies.  In other words, mythtv is looking for cable-tv channels when you are trying to feed it satellite channels.

Over at the mythtv wiki there is an article outlining setup for DVB-s cards.  Sounds like this guy used mplayer to generate a list of available channels as "channels.conf" and then fed that into the mythtv setup:

[http://www.mythtv.org/wiki/index.php/User:Grueni#Setup](http://www.mythtv.org/wiki/index.php/User:Grueni#Setup)

---

### Post by sturmey on 2007-12-10
mplayer uses a channels.conf file which I should be able to generate with dvb-utils scan, however, that also seems to fail. 

I did read something about the wacom entries in xorg.conf conflicting with the operation of the btv drivers. This leads me to two questions:
   1. why do I have wacom entries in xorg.conf? 
           I don't have a tablet PC nor do I have a tablet attached.
   2. why should wacom drivers mess up a dvb-s card, they aren't really related? 
           I'll never understand this question.

I'm going to try wiping everything out, and just installing ubuntu then adding myth afterwards. This is too bad, as it will be much more time consuming and probably wind up looking messier til I can spend a month tweaking it.

Sturmey

---

### Post by Mirco69 on 2008-04-19
Hi guys,

I would be very interested in finding out how this ends, because I'm having very similar problems.

I'm in Germany, using cable and a Satelco card. Kaffeine works (like a dream, much better than the Vista setup that the card is made for) :)

I installed Mythbuntu onto my Ubuntu 7.10 and got all the setup screens but scanning for channels just doesn't work. I tried giving Myth the path to the Kaff channels.conf - to no avail. :confused:

Thanks,

Mirco

---

### Post by Prutscher on 2008-04-19
Hi,

I am from Germany too, but my English is not very good.:popcorn:

Do you know the German MythTV-Wiki Page?
[http://www.mythwiki.de/index.php?title=Schnelleinstieg_DVB-C](http://www.mythwiki.de/index.php?title=Schnelleinstieg_DVB-C)

greetings
Prutscher

---

### Post by Mirco69 on 2008-04-20
Thanks, that was a great help! Now I found some channels and then ran into other difficulties. But I think I'll manage to work those out, once I get the backend, frontend and SQL to work together...

My biggest worry is that when I leave the backend, it tells me something about using channel three, where it has no reception.

Grüße aus Fürth,

Mirco.

---

### Post by RWN on 2008-04-20
Die Kanalliste hast Du dir aber schon mal angeschaut, wo, was wie geht.

Sorry for trying it in German.

---

### Post by DutchLoki on 2008-04-20
> Hi, I'm considering writing a complete how to guide for MythTV DVB-S (satellite). I've googled some and looked at most of the official mythTV and dedicated places for a guide about this, but found nothing good. would it be helpful for current and future users if I write one?

This will be a walk through/ how to guide that everyone can follow (no linux experience required) that includes mounting the dish to using it, configuring the satellite card, getting all available channels, using payTV channels, basicly all the works for MythTV and DVB-s.

Some topics that will be covered: 
- Hardware choise
- List of compatible cards with matrix to findout which functions are supported with that card
- Channellistings (manual and online listings)
- Diseq usage 
- Cams 
- etc.

Also (for this purpose) I was hoping everyone could mention the sites they know about the subject. This way I can save some time by including some existing texts (of cource with credits where they belong).

Thanks in advance for any suggestion you have.


Questions:
1)	what's the best place to put such a guide?
2)	Which sites do you know about this subject.


Ive posted this idea earlier today here (found out about his thread to late): 

[http://ubuntuforums.org/showthread.php?p=4751885#post4751885]("http://ubuntuforums.org/showthread.php?p=4751885#post4751885")

---

### Post by laga on 2008-04-20
Please do not discuss softcams in this forum, in the official MythTV IRC channels, in the MythTV Wiki, in the Ubuntu wiki... since we have some germans here, please don't discuss it on mythwiki.de either.

A guide for DVB would be very welcome, though. [www.linuxtv.org](www.linuxtv.org) has a list of supported cards, I guess the Ubuntu wiki has one for Ubuntu, too.

---

### Post by DutchLoki on 2008-04-20
> **laga said:**
> Please do not discuss softcams in this forum, in the official MythTV IRC channels, in the MythTV Wiki, in the Ubuntu wiki... since we have some germans here, please don't discuss it on mythwiki.de either.

A guide for DVB would be very welcome, though. [www.linuxtv.org](www.linuxtv.org) has a list of supported cards, I guess the Ubuntu wiki has one for Ubuntu, too.


Thanks for the feedback. Although softcams are in some countries legal as long their only used within your own familie, I will not discuss the extra cam section.

---

