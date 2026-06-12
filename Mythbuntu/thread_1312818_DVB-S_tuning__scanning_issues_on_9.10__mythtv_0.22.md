---
title: "DVB-S tuning / scanning issues on 9.10 / mythtv 0.22"
date: 2009-11-03
forum: Mythbuntu
---

### Post by pootle1 on 2009-11-03
I'm having problems with setting up a hauppauge dvb-s card (WinTV-Nova HD-S2) in mythtv.

I can use scan OK and it finds many,many channels, but when I try to import into mythtv, I found I got the same few channels over and over again.  By clearing everything out and starting again with a small extract from the channels.conf file, I am getting:
```
DVBChan(!:/dev/dvb/adapter6/frontend0) Error: Tune(): Setting Frontend tuning parameters failed.
     eno:  Invalid arguement (22)
```This is in a straight 9:10 ubuntu build with mythtv-backend added after building the server.

Is this really a mythtv problem or am I missing something simple?

Here's the .conf file I used;

```
EPG Background Audio.:11778:v:0:27500:0:648:4152
MATV National:12643:v:0:27500:2333:2334:54300
Pitch TV:12643:v:0:27500:2329:2330:54315
World Movies:12643:v:0:27500:2331:2332:54320
Teachers TV:12643:v:0:27500:2307:2309:54325
Elite TV:12643:v:0:27500:2345:2346:54330
OceanFinance:12643:v:0:27500:5001:5002:54345
1896:12643:v:0:27500:5001:5002:54346
54350:12643:v:0:27500:5004:5005:54350
Pitch World :12643:v:0:27500:2347:2348:54360
54325:12643:v:0:27500:0:0:1009

```

---

### Post by Neon Dusk on 2009-11-03
Have you set-up DiSEqC for the card ?
Mythbackend -> Capture Card Setup -> DiSEqC -> Create LNB and set to (Universal (Europe)

Also you could try scanning for channels directly in Mythbackend.
You'll need the starting details for a transponder.

The details for the Channel 4 transponder on Astra 2D are :-
Freq: 10714000
Polarity: h
Symbol rate: 22000000
Mod Sys: DVB-S
FEC: 5/6
Modulation: qpsk
Inversion: <leave at auto>
Rolloff: <leave at 0.35>

---

### Post by eamonn_sullivan on 2009-11-05
I had trouble at first getting DVB-S working after installing 0.22 (on a fresh install of Ubuntu 9.10). I tried the command-line scanning and import, but I eventually just used the backend-setup program. 

As mentioned earlier, make sure you set up the card correctly (with an LNB set to Europe). I used these settings to scan for channels: set Frequency to 10788000, 'Vertical' for the polarity and '2200000' for the symbol rate. The rest I left at their defaults. I got many, many channels, 95% of them crap online casino, shopping, etc., that I had to edit down.

I'm using the Hauppauge WinTV Nova S2-HD/Satellite and HD Satellite PCI TV Tuner card.

---

### Post by pootle1 on 2009-11-07
I found in mythlog that it was failing to tune the card, eventually did a rebuild of the PC and now all is working well with the card - just need a better graphics card to be able to handle HD :)

tuning using your info works very well too.

thanks Neon Dusk

---

