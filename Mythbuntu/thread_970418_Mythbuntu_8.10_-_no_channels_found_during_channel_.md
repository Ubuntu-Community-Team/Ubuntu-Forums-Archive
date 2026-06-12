---
title: "Mythbuntu 8.10 - no channels found during channel scan"
date: 2008-11-04
forum: Mythbuntu
---

### Post by root.veg on 2008-11-04
I have a problem with Mythbuntu 8.10, namely that no TV channels are found when performing a "full scan".

The following information may be useful:

(1) I'm using the 64-bit version of Mythbuntu 8.10
(2) I'm using a Hauppauge Nova-T 500 Dual tuner card
(3) MythTv successfully plays CDs, DVDs, music and videos.
(4) I'm in the UK, trying to receive the freeview digital channels. The reception in my area is poor, *but* I can definitely receive at least 10 of the Freeview channels OK using an old digibox I had hanging around.

The Problem:

When I use the channel scanner (on either of the two tuners), the signal strength remains at 0% and no channels are found, with many timeout messages being printed out. When the scan finishes there are of course no channels and so when I try and watch TV, nothing happens.

More things to note:

(6) I had the same problem previously on teh same hardware but using Mythbuntu 8.04 (32-bit version)
(7) Since I the problem remained after my fresh 8.10 install, I compiled my own drivers according to this guide:
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Installing](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Installing)
(8) Initially, nothing worked (ie, it was not even possible to set up the tuners and therefore not possible to perform a scan). I noticed in /var/log/dmesg that the firmware file being looked for was newer than the 1.10 version given in the instructions above: it needed the 1.20 version. So 

I re-compiled the drivers, this time using the 1.20 firmware version.
(9) After re-compiling with the 1.20 firmware in place, I am now able to set up the tuner cards and perform a scan again. However the problem remains, as before, that no channels are found.
(10) I've also enabled the mernel module option to turn on the internal amplifier, but this doesn't appear to have helped.

Any ideas, anyone?

---

### Post by SiHa on 2008-11-04
Maybe a stupid question, but are you selecting the correct type of card in the backend setup?

When you enter the capture card setup scree, I think the default entry highlighted is a V4L tuner card, or somesuch. Confusingly, on the line below, there is a card ID detected when the Nove-T 500 is probed, so it's easy to assume you have the correct card type. This is an analogue card, so it will attempt to find analogue channels.

It should be defined as a 'DVB MPEG Capture card V1.x'.

One easy way to check. When you perform the scan, you should be asked which country you are in, so you can select 'UK'. If you are just scanning 'Europe-west', then you almoset certainly have an analogue card setup.

BTW, you will defitely need the LNA activated, as you have done.

HTH,
Simon

---

### Post by root.veg on 2008-11-04
OK, was definitely not given the option to choose "UK" and I only remember selecting europe-west from a list. Sounds like you may be right.

Thanks for the info, I'll post back with progress...

---

### Post by db260179 on 2008-11-04
You need to create a channels.conf, then import into mythtv-setup

In a terminal, type as follows:

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-*your transmitter* > ~/channels.conf

(If you are not sure, goto 
[Freeview Checker]("http://www.freeview.co.uk/availability")

Enter your postcode to find the nearest transmitter

Then go into backend setup, then select Import channels in the channel scanner.

Hope this helps?

> **root.veg said:**
> I have a problem with Mythbuntu 8.10, namely that no TV channels are found when performing a "full scan".


---

### Post by bergqvistjl on 2008-11-05
just read that, seems as though that would cutdown on the time needed for channel scanning. Freeview lists my transmitter as 'Mendip, West', so do i put that in place of transmitter, or do i just pud 'Mendip' as thats what i see when it does a full channel scan. also, what do i do about quotes?

---

### Post by root.veg on 2008-11-05
Right, well I had a look at this and I still have the problem.

What I found out:

(1) The two tuners on my Hauppauge card are recognised in the 
"capture cards" setup as:

DVB DTV capture card (v3.x)

Not quite the same as what SiHa said but definitely not analogue.

(2) In "video source" setup I've named my source UK and it's set to use:

United Kingdon/Republic Of Ireland (Radio Times)

I left the "channel frequency table" setting at "default", in my case 
this is europe-west as defined in the "general" setup screen.

(3) When I performed a "full scan" I *was* able to choose the option "UK", and despite choosing this I still get no channels found during scanning.

I've only just read db260179's reply, but I will try those instructions tonight when I get home and report back.

---

### Post by SiHa on 2008-11-05
*if* you can get a channels.conf per db260179's reply, try the guide here: [http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php)
For testing your card outside of Myth.

I say 'if' because if it's a signal strength issue, then this scan will most likely fail as well. If this is the case - you might get away with an aerial amp (rather than a new aerial).

If you can't get a scan, you could always post your transmitter here and ask if some kind soul can post their channels.conf. Although, even if you could import this, the signal would probably be too poor for an acceptable picture.

---

### Post by db260179 on 2008-11-05
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Mendip > ~/channels.conf

~/ means home directory

> **bergqvistjl said:**
> just read that, seems as though that would cutdown on the time needed for channel scanning. Freeview lists my transmitter as 'Mendip, West', so do i put that in place of transmitter, or do i just pud 'Mendip' as thats what i see when it does a full channel scan. also, what do i do about quotes?

---

### Post by db260179 on 2008-11-05
In the setup use EIT GUIDE ONLY, not XMLTV (too complicated and troublesome). You have set it to use the XMLTV option!

When setting up the card (DVB DTV capture card (v3.x)), make sure one tuner only has the 'Active Scan' turned on, if both have this option turned on, it will crash the box or prevent a channel scan. Also make sure you turn on the LNA (all of this is found in the mythtv-setup, capture-cards)

> **root.veg said:**
> Right, well I had a look at this and I still have the problem.

What I found out:

(1) The two tuners on my Hauppauge card are recognised in the 
"capture cards" setup as:

DVB DTV capture card (v3.x)

Not quite the same as what SiHa said but definitely not analogue.

(2) In "video source" setup I've named my source UK and it's set to use:

United Kingdon/Republic Of Ireland (Radio Times)

I left the "channel frequency table" setting at "default", in my case 
this is europe-west as defined in the "general" setup screen.

(3) When I performed a "full scan" I *was* able to choose the option "UK", and despite choosing this I still get no channels found during scanning.

I've only just read db260179's reply, but I will try those instructions tonight when I get home and report back.

---

### Post by root.veg on 2008-11-05
cool, thanks for the pointers - will try this late tonight once I get home :-)

---

### Post by root.veg on 2008-11-06
OK, still not working - summary so far:

(1) The two tuners are set up so that only the first one is used for "active" EIT scan.

(2) The video source is now configured to use the EIT guide only.

(3) I tried the scan utility after finding out that my local transmitter is Winter Hill (I live in Manchester). But it gives me an error I don't understand: which "frontend" is it talking about?:

```
root@pisco-sour# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > ~/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy
```

---

### Post by db260179 on 2008-11-06
So far so good. You must stop the mythtv-backend first (sudo /etc/init.d/mythtv-backend stop)

Then do the scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > ~/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill

Then start the backend again(sudo /etc/init.d/mythtv-backend start), then run mythtv-setup again, then try to import the channels.conf

> **root.veg said:**
> OK, still not working - summary so far:

(3) I tried the scan utility after finding out that my local transmitter is Winter Hill (I live in Manchester). But it gives me an error I don't understand: which "frontend" is it talking about?:

```
root@pisco-sour# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > ~/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy
```

---

### Post by root.veg on 2008-11-06
I'll try that solution tonight, thanks for the tip...

---

### Post by root.veg on 2008-11-06
Well I'm beginning to think it's just a signal strength issue now - this is what I got using the command line scan tool:

```
root@pisco-sour# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > ~veg/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 754166670 0 3 9 1 0 0 0
>>> tune to: 754166670:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 754166670:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

Anyone have any bright ideas? Think I'm going to have to lug my new box to someone else house (who I know has good reception) in order to test this...

---

### Post by SiHa on 2008-11-07
Do you have anything else (other TV's / set top boxes) connected to the aerial? Try unplugging them.
Do you have any passive splitters on the line, if possible remove those, as each splitter will introduce a signal loss, especially if it's a cheap one that isn't impedance matched (ie not 75ohm).
If you have an old video recorder, you can use the loop-through as a signal amplifier.
If all else fails, boosters are cheap...

---

### Post by db260179 on 2008-11-07
Do you have a working digital freeview working in your house?

Is so, go into you box or tv, and see what transmitter it is using, sometimes there is more than one choice for a transmitter.

> **root.veg said:**
> Well I'm beginning to think it's just a signal strength issue now - this is what I got using the command line scan tool:

Anyone have any bright ideas? Think I'm going to have to lug my new box to someone else house (who I know has good reception) in order to test this...

---

