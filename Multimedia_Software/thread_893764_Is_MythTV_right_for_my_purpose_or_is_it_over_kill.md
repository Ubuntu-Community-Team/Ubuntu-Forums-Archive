---
title: "Is MythTV right for my purpose or is it over kill?"
date: 2008-08-18
forum: Multimedia Software
---

### Post by clancymf on 2008-08-18
I currently pay alot of money for hi-def cable and DVR.  

I wanted to get a video capture card so I could burn to disk some shows for my son without having to clog our DVR listing. Figure if I drop about $50-$75 dollars for a capture card I could make this happen with MythTV.  However, after reading many of the posts and information on the internet it appears that everyone using mythtv are getting there content free over the air (OTA) tv and use an external antenna.  

I havent seen one person who wants to take an existing cable outlet and plug it into their computer to capture the information.  Which makes me wonder if this would even work and if so does a "special" capture card have to be used to translate the signal from the cable company. 

Thanks!

---

### Post by KindredCharles on 2008-08-18
> **clancymf said:**
> I currently pay alot of money for hi-def cable and DVR.  

I wanted to get a video capture card so I could burn to disk some shows for my son without having to clog our DVR listing. Figure if I drop about $50-$75 dollars for a capture card I could make this happen with MythTV.  However, after reading many of the posts and information on the internet it appears that everyone using mythtv are getting there content free over the air (OTA) tv and use an external antenna.  

I havent seen one person who wants to take an existing cable outlet and plug it into their computer to capture the information.  Which makes me wonder if this would even work and if so does a "special" capture card have to be used to translate the signal from the cable company. 

Thanks!

I bought a card a few days ago, my plan was to capture cable like this, I havn't gotten around to setting it up but when I finish i'll tell you how it went.

---

### Post by wyliecoyoteuk on 2008-08-18
You can either:
A) if you have a coax or composite etc output from your cable box, you may be able to feed this into an analogue TV capture card.
B) use a cable tv card (DVB-C) success will depend where you live and your provider.


There are 3 main types of DVBTV in europe
DVB-C (cable)
DVB-S (satellite)
DVB-T (Terrestrial)

Other standards are used by other countries.

---

### Post by Loaded.len on 2008-08-18
I have cable television in Canada.  Standard Def, but with better tuner cards and a slightly faster processor I could do HD with no trouble.  As it is now. I have two Haupaugge PVR 150's - cable is split and goes into each card.  MythTV works like a dream, however since Zap2It no longer offeres free listings I have to pay a measly $15.00 USD per year for schedules direct...SD is well worth the money, it's never let me down. My whole family absolutely loves our Mythbox.

---

### Post by clancymf on 2008-08-19
Thanks everyone for the comments.  I think I will look into getting a Haupaugge PVR 150 and testing it out. 


@ Loaded.len - what type of front end are you using?

---

### Post by Loaded.len on 2008-08-19
It's a combo backend/frontend at the moment. 

Giga-byte motherboard (GA-73PVM-S2H)
Celeron 3.06
2GB RAM
2 x PVR 150
Nvidia 7100GS
2 x 250GB HDD

I'm in the process of doing some upgrades.  I'll be putting a faster proc, 2 x HD tuners (probably pcHDTV-5500), and expanding my FreeNAS box to at least a terabyte. 

If you use Mythbuntu, I would recommend doing manual paritioning.  Give yourself about 10GB for / (Ext3), a resaonable Swap (1 - 1.5 times your RAM) and the rest as XFS mounted at /mythtv (or /storage or whatever else suits your fancy) 

The guided partitioning in 8.04 uses all Ext3 and puts the recordings, videos, pictures, etc all in /var/lib/mythtv.  This is fine except for Ext3 doesn't handle large files as well as XFS.

Let me know if there's anything else I can help you with.

---

