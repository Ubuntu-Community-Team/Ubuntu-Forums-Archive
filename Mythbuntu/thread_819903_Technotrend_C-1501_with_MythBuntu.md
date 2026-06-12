---
title: "Technotrend C-1501 with MythBuntu"
date: 2008-06-05
forum: Mythbuntu
---

### Post by DutchLoki on 2008-06-05
Can anyone tell me if the technotrend C-1501 works with MythBuntu? I've searched the driver threads about it and it seems very new. 

[http://www.spinics.net/lists/linux-dvb/msg25369.html](http://www.spinics.net/lists/linux-dvb/msg25369.html)

[http://www.linuxtv.org/wiki/index.php/DVB-C_PCI_Cards](http://www.linuxtv.org/wiki/index.php/DVB-C_PCI_Cards)

Can anyone tell me if this driver is includded in the laters version of MythBuntu, retrieved automatically or if I need to install it manually?

I also would like to hear if you have experience with this card and if its any good.

---

### Post by DutchLoki on 2008-06-07
update: there working on a driver, there is experimental support.

[http://marc.info/?l=linux-dvb&w=2&r=1&s=c-1501&q=b](http://marc.info/?l=linux-dvb&w=2&r=1&s=c-1501&q=b)

---

### Post by DutchLoki on 2008-06-09
> **DutchLoki said:**
> update: there working on a driver, there is experimental support.

[http://marc.info/?l=linux-dvb&w=2&r=1&s=c-1501&q=b](http://marc.info/?l=linux-dvb&w=2&r=1&s=c-1501&q=b)


There seems to be a first version available: 
[http://marc.info/?l=linux-dvb&w=2&r=1&s=c-1501&q=b](http://marc.info/?l=linux-dvb&w=2&r=1&s=c-1501&q=b)

---

### Post by Jonsson84 on 2008-06-11
I'm really interested in this card, has anyone tested the card with the experimental drivers and can tell us how good/bad it works(and if it works in mythtv) =)

/Jonsson

---

### Post by erland on 2008-06-23
> **DutchLoki said:**
> There seems to be a first version available: 
[http://marc.info/?l=linux-dvb&w=2&r=1&s=c-1501&q=b](http://marc.info/?l=linux-dvb&w=2&r=1&s=c-1501&q=b)

Has anyone tried the experimental support for C-1501 yet ?
Does the CI interface work also or does it only work with unencrypted free channels ?

---

### Post by captain-nono on 2008-07-30
**Intro:**
Here are my findings with the Technotrend Budget c-1501 up to this moment: After reading trough some posts on the MytTV and Mythbuntu forums I gathered enough courage to order two brand new c-1501 dvb-c cards and the needed CI interfaces that go with them. Being a total newbie in Ubuntu world it was quite a gamble considering the fact that there is not much to find about the c-1501 being supported in MythTV apart from some experimental driver patches that supposed to work. I ordered the cards at [www.dvbshop.net]("http://www.dvbshop.net") in Germany and three days later I received a box from the mailman.

**Hands on:**
After I received the cards I immediately started to put one in my current htpc. I found an old hard drive to install Mythbuntu on. Ill explain what I did to get the card visible in the MythTV&#8217;s configuration.

First step was to install the video 4 linux drivers:
[http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers) 

1. Load up a terminal window if you are in the graphic interface.
2. Type in the following to install gcc, mercurial and the kernel headers:

*sudo apt-get install build-essential mercurial linux-headers-`uname -r`*

3. Move to the /usr/src/ folder with:

*cd /usr/src*

4. Download the latest V4L drivers with:

*sudo hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)*

5. Move into the newly created folder with

*cd v4l-dvb*

6. Now start the building process with:

*sudo make*

7. And finally we install these drivers with:

*sudo make install*

8. Reboot your computer and the newer V4L drivers will be used.

This should me all! I found out that the patches found on the internet (c-1501.patch / c-1501_try2.patch) where already integrated into the current budget-ci.c driver which was downloaded with the V4L drivers.

After a reboot I could go into the MythTV configuration and select the c-1501 which is now being recognised by it&#8217;s chipset and pops up as: &#8220;Philips TDA10023 DVB-C Subtype: DVB-C&#8221;. If I now go to the channel list in the configuration of MythTV the button for scanning channels is still greyed out?

This is basically where I am stuck. Since I live in the south of the Netherlands, Ziggo is our cable provider (formerly @home &#8220;Horst aan de Maas&#8221; region). Which gives me an extra obstacle to overcome before I can start enjoying watching tv on my Mythbox as you can read here: [http://www.mythtv.org/wiki/index.php/Channel_tuning_broken_with_DVB-C]("http://www.mythtv.org/wiki/index.php/Channel_tuning_broken_with_DVB-C") .
I followed the instructions, and started scanning for channels but nothing came up.

**Technical details:**
Technotrend Budget C-1501 Rev. 1.0
Technotrend Budget CI Rev. 1.0A
AlphaCrypt Classis CAM module

Frequency / Modulation type / Symbol Rate 
----------------------------
276000,64QAM,6875000 
268000,64QAM,6875000 
252000,64QAM,6875000 
436000,64QAM,6875000 
444000,64QAM,6875000 
420000,64QAM,6875000 
452000,64QAM,6875000 
380000,64QAM,6875000 
364000,64QAM,6875000 
372000,64QAM,6875000 
460000,64QAM,6875000 
396000,64QAM,6875000 
292000,64QAM,6875000 
404000,64QAM,6875000 
284000,64QAM,6875000 
388000,64QAM,6875000 
412000,64QAM,6875000 
682750,64QAM,6875000 
658750,64QAM,6875000 
562750,64QAM,6875000 
356000,64QAM,6875000 
428000,64QAM,6875000 
260000,64QAM,6875000 
690000,64QAM,6875000

Any help on where I might be missing something would be greatly appreciated.

---

### Post by captain-nono on 2008-07-31
I managed to get my c-1501 working with Kaffeine. I used the folowing transponder file:
C 276000 6875000 NONE QAM64 
C 268000 6875000 NONE QAM64 
C 252000 6875000 NONE QAM64 
C 436000 6875000 NONE QAM64 
C 444000 8750000 NONE QAM64
C 420000 6875000 NONE QAM64
C 452000 6875000 NONE QAM64 
C 380000 6875000 NONE QAM64 
C 364000 6875000 NONE QAM64 
C 372000 6875000 NONE QAM64 
C 460000 6875000 NONE QAM64 
C 396000 6875000 NONE QAM64 
C 292000 6875000 NONE QAM64 
C 404000 6875000 NONE QAM64 
C 284000 6875000 NONE QAM64 
C 388000 6875000 NONE QAM64 
C 412000 6875000 NONE QAM64 
C 682750 6875000 NONE QAM64 
C 658750 6875000 NONE QAM64 
C 562750 6875000 NONE QAM64 
C 356000 6875000 NONE QAM64 
C 428000 6875000 NONE QAM64 
C 260000 6875000 NONE QAM64 
C 690000 6875000 NONE QAM64

It seems to work correct. Even the encrypted channels work great.

I also received a channels.conf file from someone in my cable region. I imported the file into MythTV. When I start the scan it finds a lot of channels but non of them seem to work. I get a message like "cant get a lock". Am I doing something wrong? Can I do a scan in MytTV based on the above transponder list? I'm struggeling with this promblem for four days now :(

Please help?
(btw is there a method for converting [channels.dvb ]("http://www.psychopater.nl/channels.dvb")from Kaffeine to a channels.conf file?)

---

### Post by CrimsonRider on 2008-08-05
I am also using the TT-1501 with CI module. I am going to follow those instructions and see what can be done.

I am using Ziggo as well, ex-Casema region, with the Digital Decoder card I should be able to watch digital TV. I'll keep it updated.

---

### Post by Alfaroid on 2008-08-06
> **captain-nono said:**
> I also received a channels.conf file from someone in my cable region. I imported the file into MythTV. When I start the scan it finds a lot of channels but non of them seem to work. I get a message like "cant get a lock". Am I doing something wrong? Can I do a scan in MytTV based on the above transponder list? I'm struggeling with this promblem for four days now :(

Please help?


Nederlands is wat makkelijker:
Nadat je via de mythtv-backend heb gescand naar kanalen gooit mythtv op de een of andere manier de dtv-multiplex tabel in de war.
Deze multiplex tabel kun vinden in de mysql database. Als je phpmyadmin installeert: sudo apt-get phpmyadmin kun daarna via je browser bij de database komen [http://localhost/phpmyadmin](http://localhost/phpmyadmin). Login hier in en selecteer de database mythconverg.
Selecteer de tabel dtv-multiplex en klik browse/verkennen.
In deze tabel moet in de rijen bij het netwerkid jouw id staan
Een lijst vindt je hier [http://www.digitalekabeltelevisie.nl/techniek/tvhome.shtml](http://www.digitalekabeltelevisie.nl/techniek/tvhome.shtml)
Bij de frequenties zul je zien dat deze staan op b.v. 323000000 ipv 313000000 (=Ziggo zwolle)

Als je deze tabel helemaal aanpast is het probleem verholpen.
LET OP: als je weer scant naar zenders in mythtv-backen wordt de tabel weer door elkaar gegooid.

Hoop dat dit heeft geholpen

Groet,

Alfaroid

---

### Post by CrimsonRider on 2008-08-06
Dutch or English, I don't care, both work for me.

But, for the life of me, I can't get it to work at all. I am in Delft, Ziggo now, but ex-casema region. And all I can get is some stream from Den Haag TV.

I use the 1501-C with Alphacrypt, hope my smartcard is inserted right, any way to check if the Alpha is working?

Anyways, I scan and scan and scan, and I find

```
# file automatically generated by w_scan
# (http://wirbel.htpc-forum.de/w_scan/index2.html)
# freq sr fec mod
C 386000000 6875000 AUTO QAM64
C 474000000 6875000 AUTO QAM64
```

And that yields;

```
Den Haag TV:474000000:INVERSION_AUTO:6875000:FEC_AUTO:QAM_64:4131:4129:5001
```

Nothing more. Help? Anyone? Please? This is pitifull. I am a card-carrying nerd, and can't get it to work :(

---

### Post by Alfaroid on 2008-08-07
Your frequenties are here: [http://www.digitalekabeltelevisie.nl/techniek/casema_multikabel.shtml](http://www.digitalekabeltelevisie.nl/techniek/casema_multikabel.shtml)
Scroll down to te bottom of the page where is says Ziggo.
These are the frequenties you should use.

I personally scan for channels from mythtv-backend (Channel editor). Try this once please.
1. Open the channel editor
2. Select the soure for your digital channels
3. Select Scan for channels
4. Select "Volledige scan (afgestemd) (assuming your box is NL)
5. Put in the frequentie 450000000
6. Put in Signal rate 6875000
7. Select QAM 64
8. Select Next/Volgende to scan for channels

This should result in finding the channels: Nederland 1, 2, 3, MGM, RAI Uno.

If it does close the backend and try watching the channels from the frontend. If a pop-up appears mentioning "Kan niet vergendelen" then see my previous post.

Groeten,

Alfaroid

---

### Post by CrimsonRider on 2008-08-07
That didn't quite work, but I did get it to work.

I used the nl-casema file from examples to run a dvbscan with. That yielded a channels.conf file that I could import into MythTV, and yay, profit!

---

### Post by avocade on 2008-08-10
> **Alfaroid said:**
> Your frequenties are here: [http://www.digitalekabeltelevisie.nl/techniek/casema_multikabel.shtml](http://www.digitalekabeltelevisie.nl/techniek/casema_multikabel.shtml)
Scroll down to te bottom of the page where is says Ziggo.
These are the frequenties you should use.

I personally scan for channels from mythtv-backend (Channel editor). Try this once please.
1. Open the channel editor
2. Select the soure for your digital channels
3. Select Scan for channels


On point 3, it's totally grayed out for me. Can't click it! It's finding the card alright (AverTV DVB-T 771) but still disabled. Worked fine on Knoppmyth for two years...

---

### Post by jaffamuffin on 2008-08-16
I got a 1501 DVB-C from dvb shop  and tried to get it working with an virgin media feed (ex ntl) and following the very good instrcutions in a post above got it installed.

Using Mythubuntu i386 desktop 8.04.1 on a asrock board with e2140 cpu.

Managed to get it tuned in using scan transponders after I had filled the details in freq, qam symb rate etc) and It detected all the channels, and also started to populate the guide wth data 'over the air' sweet!

Anyway, it worked for about 30 mins watching live tv now when ever I watch live tv it gives me the error on screen "Error encountered while displaying video?"  

I have searched alot and haven't found any reasonable fix for this, aprt from an old build of mythtv that would try to read the ring buffer but the backend would change the filename, so the front end couldn't find it and display it. But that bug is apparently long fixed.   

Any thoughts?  

ps. The picture on the DVB-C signal was really -really- good.

---

### Post by DutchLoki on 2008-08-19
> **Alfaroid said:**
> Als je phpmyadmin installeert: sudo apt-get phpmyadmin kun daarna via je browser bij de database komen [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Noticed you made a typo ;), the install command was missing: 

sudo apt-get install phpmyadmin


also for who does not like to install unneeded software on your system can also start mysql from the command promt by typing mysql. from here you can execute you sql statements.

---

### Post by DutchLoki on 2008-08-21
> **avocade said:**
> On point 3, it's totally grayed out for me. Can't click it! It's finding the card alright (AverTV DVB-T 771) but still disabled. Worked fine on Knoppmyth for two years...

did you walk through al the setups steps like configuring the tuner card, videosources, etc?

---

### Post by malaTG on 2008-08-21
Hi everyone,

A question. I only have a production machine which has a pvr-150 card running inside. 

If I insert my c-1501 card inside this machine and compile the drivers as this guide suggest, which problems should I anticipate? 

1. Will my pvr-150 card still work?

2. Will there be any problems upgrading to ubuntu 8.10 when the driver probably comes with the distribution?

3. Should I uninstall any packages before compiling the new driver?

4. Is there anything else I should think about?(I live in Sweden but that is probably not relevant....)

Thx in advance!

Marcus

---

### Post by Eldis on 2008-08-22
I've just ordered 2 of these cards, and pre-combiled myself a list of possible problems I might encounter. I'm hoping I'll get these up and running fast. WAF factor goes down really fast when something isn't working ;).

---

### Post by DutchLoki on 2008-08-22
> **malaTG said:**
> Hi everyone,

A question. I only have a production machine which has a pvr-150 card running inside. 

If I insert my c-1501 card inside this machine and compile the drivers as this guide suggest, which problems should I anticipate? 


I had my pvr 350 in my machine when testing the c-1501. for your information the pvr 350 uses the same chipset only had an different kind of video out. I had no trouble at al getting the c-1501 to work. Only needed to install the latest video4linux drivers (v4l). Also the pvr 350 just kept working as before.  

> 
1. Will my pvr-150 card still work?

yes
> 
2. Will there be any problems upgrading to ubuntu 8.10 when the driver probably comes with the distribution?

Have not tried that with an release candidat of 8.10 but i don't beleave it will give any trouble.

> 
3. Should I uninstall any packages before compiling the new driver?

only your v4l drivers if you have them installed already. Just follow the instructions on the v4l site from the url mentioned earlier in this forum. 

> 
4. Is there anything else I should think about?(I live in Sweden but that is probably not relevant....)


can't think of anything except the problem with scanning non-standard dvb cable providers as discussed here. Hopefully yours is standard. By the way the C-1501 one is great and unbelievable cheap. I've installed 8 of those cards now (6 by friends) and al work great.

Let me know if you running in any trouble, hopefully your installations will be as easy as mine.

---

### Post by malaTG on 2008-08-24
Hi DutchLoki,

Thank you very much for your answers everything works perfect. I haven't got my program card yet so I can't try most of my channels but there are some testchannels that work :-)

I have one more question. When I use an analog card I use xmltv to get my information. 

1. Now as I understand it with the settings I can both get the information from xmltv and EIT at the same time for a channel om my new card? 

2. What are the advantages/drawbacks of doing in one or the other way? If I mix the data will mythtv get confused and record a program on both my pvr-150 and my new dvb card because the information isn't exactly the same? etc.

Thank you in advance!

Marcus

---

### Post by DutchLoki on 2008-08-24
> **malaTG said:**
> Hi DutchLoki,

Thank you very much for your answers everything works perfect. I haven't got my program card yet so I can't try most of my channels but there are some testchannels that work :-)

I have one more question. When I use an analog card I use xmltv to get my information. 

1. Now as I understand it with the settings I can both get the information from xmltv and EIT at the same time for a channel om my new card? 

yes that works fine.

> 
2. What are the advantages/drawbacks of doing in one or the other way?

none as far I noticed.

> 
If I mix the data will mythtv get confused and record a program on both my pvr-150 and my new dvb card because the information isn't exactly the same? etc.

mythtv always chooses one card, the one with the highest prio. Mythtv sets prios for you when you add tuner cards (you can change these in the configuration menu).  

The epg data can be different, but you need to choose which one is better than the other. I overwrite my xmltv data with the data from my epg deliverd from my dvb cards. This way I have the best of both worlds. I believe this is default... but not sure. 

> 
Thank you in advance!

Marcus

your welcome.

---

### Post by Eldis on 2008-09-05
I got my cards working pretty fast using the newest v4l-dvb but problem is I can't get sasc-ng to work anymore. Any idea what kernel would natively support these cards ? Since my sasc compiles nicely if I don't link the v4l-dvb module I just installed but when I do I get segfault and a kernel oops.

Or other ideas I'm at a loss.

EDIT: I'm up and running again the solution was at: [http://dvbn.happysat.org/viewtopic.php?t=46019](http://dvbn.happysat.org/viewtopic.php?t=46019)
it was a bit troublesome but I hope this shortens the solution time for some other person with the same problem.

---

### Post by Ashrael on 2008-09-17
@ALL: Can you give me a quality assessment for your cards please? I am thinking about buying a dvb-c card WITH Ci, so please mention this too...

Thank you...

---

### Post by DutchLoki on 2008-10-01
> **Ashrael said:**
> @ALL: Can you give me a quality assessment for your cards please? I am thinking about buying a dvb-c card WITH Ci, so please mention this too...

Thank you...

sure, what specifics would you like to know?

---

### Post by Ashrael on 2008-10-04
@dutchloki: I would like to know if it gives good quality picture, if it can take a ci/cam that will work in the netherlands, how the driver is etc...I am looking at buying a dvb-t/dvb-c card with dual tuner if possible...


tia!

---

### Post by DutchLoki on 2008-10-10
> **Ashrael said:**
> @dutchloki: I would like to know if it gives good quality picture, if it can take a ci/cam that will work in the netherlands, how the driver is etc...I am looking at buying a dvb-t/dvb-c card with dual tuner if possible...


tia!


The C-1501 gives excellent picture quality and the CI support is one of the best under linux. Keep in mind when buying a CAM module for encrypted cable television you need the alphacrypt classic, not the cheaper light one. Also UPC cable decoding is not available. If you're with ziggo all is fine.

I have no experience with dualtuners on one card, but I'm using a dualtuner setup with multiple technotrend cards, so this is supported... ofcourse. 

Its also possible to record multiple channels from only one card, this is called multirec in the mythtv community. This is posible because the card tunes in to group of channels(streams) and passes this to your computer. So as long 2 our more channels are in one group, your computer can record/show these using only one card. most groups contain 6 channels and there are around 29 groups. 

Hope this answers your questions.

---

### Post by Ashrael on 2008-10-23
@DUTCHLOKI: great news! thank you!

---

### Post by MagnusL on 2008-10-27
> **DutchLoki said:**
> Its also possible to record multiple channels from only one card, this is called multirec in the mythtv community. This is posible because the card tunes in to group of channels(streams) and passes this to your computer. So as long 2 our more channels are in one group, your computer can record/show these using only one card. most groups contain 6 channels and there are around 29 groups. 

Hope this answers your questions.

Hi!

I have a TT C-1501, running ubuntu hardy heron, and a CI module that i bought with the card. However, I can only view one channel at the time. This thing with channels being in groups - how can I figure this out and utilize it? Right now, I cannot have two frontends watching Live TV at the same time, same channel. 

Or does it only apply to recording, not watching live TV?

Magnus

---

### Post by DutchLoki on 2008-10-28
> **MagnusL said:**
> Hi!

I have a TT C-1501, running ubuntu hardy heron, and a CI module that i bought with the card. However, I can only view one channel at the time. This thing with channels being in groups - how can I figure this out and utilize it? Right now, I cannot have two frontends watching Live TV at the same time, same channel. 

Or does it only apply to recording, not watching live TV?

Magnus

please read my previous post about multirec. You can look in your channel table and multiplex table to find out which channels are in the same "group". 

Also i'm not sure if multirec is enabled by default.... you should look into that to.

---

### Post by malaTG on 2008-11-15
> [QUOTE]
Quote:
2. Will there be any problems upgrading to ubuntu 8.10 when the driver probably comes with the distribution?

Have not tried that with an release candidat of 8.10 but i don't beleave it will give any trouble.[/QUOTE]

Ok so now I am thinking of upgrading to 8.10 release. Have anyone tried this after applying the above changes to their system? Did it work? Was there any problems?

/mala

---

### Post by DutchLoki on 2008-11-15
> **malaTG said:**
> Ok so now I am thinking of upgrading to 8.10 release. Have anyone tried this after applying the above changes to their system? Did it work? Was there any problems?
/mala

Hi malaTG, I'm not sure about what changes you're talking about, but the c-1501 works fine under 8.10. I only tried 8.10 for a few days though. I'm now running on Ubuntu 8.04 and custom MythTV install because of the long term support (lts). 

Hope this anwers your question.

---

