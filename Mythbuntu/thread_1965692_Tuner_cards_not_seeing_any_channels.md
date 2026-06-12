---
title: "Tuner cards not seeing any channels"
date: 2012-04-26
forum: Mythbuntu
---

### Post by zzz1827 on 2012-04-26
About 5 months ago, I noticed that some shows were not being recorded.  Those shows were on higher channels and not necessarily shows I cared about.  Come February 2012, I noticed that shows on lower channels were not recording.  The problem got worse in March and April until it can't record anymore shows.

Sometimes restarting the Backend solved the problem.  Sometimes removing the DVB cards in Myth-Backend Setup and rescanning for channels solved the problem...  for a day or two.

So I began to troubleshooted the problem.  I thought one of my two 5 year old pchdtv-5000 cards was going bad so I bought another.  The new one isn't working either.

Now, I can't get ANY of the channels to be seen by any of my pchdtv cards much less get a signal lock.  The cards can be configured.  The cards can be opened by Mythbuntu.  I have been using MythTV for 5 years with these cards.  My first Mythbuntu installation was 10.10 a year or so ago; it went simple and I had no problems configuring nor using the cards back then.

I am getting my TV stream over the airwaves (ATSC,) not from cable.  I have tested the video signal.  All channels work great if I run the same coax cable to a Digital TV converter box.  Although I am in a major US city, I have a Signal Booster; I swapped it out without any success.

I have looked over my pchdtv-5000 tuner cards very carefully.  I don't see nor smell any burned out capacitors.

I have clean installed Mythbuntu 10.10(MythTV .23.1) and 11.10(MythTV .24) to a clean 80 Gig hard drive., configured Myth-Backend Setup, scanned for channels and get nothing.  I have not tried Mythbuntu 12.04 yet.

Maybe I have just forgotten how to properly configure the pchdtv card.  I have attached a picture of my configuration.  If anyone sees anything wrong, please tell me.

Although the computer is old and slow, it should not be a problem as Primary Backend machine.

I'm stumped and don't know what to do to troubleshoot the problem anymore. Any suggestions whether it be hardware or software are welcome.

Rob
Primary Backend Configuration:
1GHz AMD Athlon 64 Processor
1Gig RAM
2 pchdtv-5000 tuner cards
1 pchdtv-3000 tuner card
ATSC over the airwaves video sources

---

### Post by klc5555 on 2012-04-26
Usually when you start getting a slow to complete fail over time like this, the cuplrit tends to be hardware rather than software. However, that still has to be clearly established here.

You have swapped the pchdtv5500 for a new one. No effect. The tuner card(s) would therefore appear likely not to be faulty.

You have "swapped out" the signal amp. Does this mean you tried with and without a signal amp? If the sig amp failed and you actually need one for your tuner cards (they generally require stronger signals than dedicated TVs), then just swapping out the sig amp without replacing would not necessarily detect the problem. If, on the other hand, you just replaced one sig amp with another, you may be missing the possibility that signal strength in your area has improved, and very strong signals being further amplified are swamping your card(s). I can't imagine that there's a major hardware issue with your PC itself --symptoms would have been different and more severe than being unable to tune a pchdtv card. However, it is known that tuner cards can be a bit sensitive as to which PCI slot they are in (and how well they are seated), with the slot closest to the video card slot being prefered on older machines. Also your cards may require more time to tune the signals than is being given to them. (As mentioned in the Mythtv manual here: [http://www.mythtv.org/wiki/User_Manual:Setting_up_DVB-T_%28terrestrial%29](http://www.mythtv.org/wiki/User_Manual:Setting_up_DVB-T_%28terrestrial%29) )

On the software side, the configuration screen you posted indicates the dvb tuner is likely found correctly by the system, but not whether you have scanned on the correct frequency spread in Input Connections (i.e. 8-VSB I would imagine), nor whether the correct channel frequency table for your area was set in Video Sources for your Video Source. I'm sure that lspci, dmesg, and lsmod output will indicate the card is detected and the drivers are loaded. You might then wish to see whether you can scan for channels and compose a channels.conf file using the standard dvb-apps tools found at linuxtv.org: [http://linuxtv.org/hg/dvb-apps](http://linuxtv.org/hg/dvb-apps)

If a scan can be completed successfully by the dvb tools, you may wish to try using such a composed channels.conf file in lieu of scanning in mythtv. Or see whether one of the simpler tv-display apps available can either scan the tuner card itself or tune using the channels.conf file you just generated. Xine, for example can do this, or any one of several simpler TV apps described here: [http://linuxappfinder.com/multimedia/television](http://linuxappfinder.com/multimedia/television)

The whole point of all of this is to narrow down whether your issue is hardware or software. If hardware, then the issue is beyond this forum's scope. If software and Mythbuntu, then whether the issue is with the application Mythtv or with the OS Ubuntu needs to be figured out.

---

### Post by zzz1827 on 2012-05-10
Update on my situation.  I have decided that my computer equipment just doesn't like playing together anymore.  In the 30 years I've been tinkering with computers, I have had 4 times where known good equipment just stops working together.  I think this is one of those times...

If I put either one of the pcHDTV-5000 tuners in my computer, it will open the card but will not lock on any channels.

If I put both pcHDTV-5000 tuners in my computer, only one will open.  That one will also get a signal lock and see channels.  I can watch those channels either live or via a recording as long as the recording occurs within a few hours of the channel edit.  Within 24, the 5000 tuner is no longer getting a lock nor seeing channels.

The pcHDTV-3000, whether by itself or with other cards, will not lock on any signal.

So I went out and bought a couple of HDHomeRun tuners.  I removed my tuners from inside the computer.  For the past week, everything is recording fine.

My computer no longer likes the ptHDTV-5000 tuners and the tuners no longer want to work alone.

klc5555,

Thank you for your reply.  It is EXACTLY the kind of reply I was looking for.

Rob

---

### Post by klc5555 on 2012-05-10
Sorry you had to buy additional hardware, but at least you're up and running. The most important immediate result.

However, keep those hd5500 cards around. I suspect they're OK and will prove useful to you later.

Also, keeps tabs on any other cards you may have currently plugged into your PCI bus for unusual behavior. It wouldn't be the first time a motherboard has started to go flaky bit by bit, before dying completely.


All the best.

---

