---
title: "Recommendation for HDHOMERUN?"
date: 2009-10-19
forum: Mythbuntu
---

### Post by luigidk on 2009-10-19
In relation to my post below (avermedia issues) -
[http://ubuntuforums.org/showthread.php?p=8130335#post8130335](http://ubuntuforums.org/showthread.php?p=8130335#post8130335)

I am considering moving to an alternative solution.

I would still use my PVR-150 for digital cable capture - but for my direct from cable (no cable box) that I was using the AVERMEDIA card on - would an HDHOMERUN work well?

Would it be a 1-1 swap with the avermedia card?  

Does 9.04 of MythBuntu handle HDHOMERUN out of the box?  

Thanks for the help!

---

### Post by bsntech on 2009-10-19
The HDHomeRun does work with MythTV.  In the backend capture card setup, there is an option for this in the drop-down box.

the HDHomeRun also will have two tuners in it - so you could potentially use it for both - although I'm sure you'll want to keep the PVR-150 in the box for your remote control.

---

### Post by luigidk on 2009-10-19
It seems to me that an external box like HDHOMERUN is better solution than adding an internal card?  If I change/upgrade my computer - the HDHOMERUN just moves.  

Will it take some of the processing off of my computer?  I have an AMD 3700 processor - with 1gb of RAM and I am not real interested in upgrading for HD.  Thinking the HDHOMERUN could be a good bridge until I need to update!

---

### Post by uncle hammy on 2009-10-19
If I could pro-create with my HDHomeRun(s), I would :guitar:

FWIW

---

### Post by luigidk on 2009-10-19
Well it seems the HDHOMERUN is an easy and fairly cost effective way to solve my avermedia card issue!

So looking at configuration - I have hopefully 1 simple question:

Note - took out question on connecting to ethernet - see that it plugs into my router or switch...

---

### Post by luigidk on 2009-10-19
I new question...

I use Comcast and the DCT6200 set top box...

With an HDHOMERUN - can I replace the DCT6200 with it?  Use 1 tuner port for where my DCT6200 went into my pvr-150 - and 1 tuner port for my digital cable (coming in from comcast - that is NOT coming through my cable box today).  (q2: anyone using HDHOMERUN for Comcast - what are the settings for channel scanning (qam-256 and broadcast/cable or ???)

seems if i use the HDHOMERUN for all my MYTHTV capture - then I could continue to use the DCT6200 for viewing straight to my TV monitor - thus letting me record on two separate channels via HDHOMERUN and watching stations on the DCT6200 ???

Too easy?

---

### Post by blackoper on 2009-10-19
> **luigidk said:**
> I new question...

I use Comcast and the DCT6200 set top box...

With an HDHOMERUN - can I replace the DCT6200 with it?  Use 1 tuner port for where my DCT6200 went into my pvr-150 - and 1 tuner port for my digital cable (coming in from comcast - that is NOT coming through my cable box today).  (q2: anyone using HDHOMERUN for Comcast - what are the settings for channel scanning (qam-256 and broadcast/cable or ???)

seems if i use the HDHOMERUN for all my MYTHTV capture - then I could continue to use the DCT6200 for viewing straight to my TV monitor - thus letting me record on two separate channels via HDHOMERUN and watching stations on the DCT6200 ???

Too easy?

Hdhomerun won't work at getting all your cable channels. While the channels are in standard qam256 modulation, almost all channels are encrypted. You will only be able to see unecrytped local channels usually (if you get more it won't be for long).

It's not an analog capture card so running input into it from the cablebox won't work either.
Only way to get good capture of a encypted dig channels/hd channels is the hd-pvr capture card from hauppauge (component capture) or if you don't need hd running an svideo and rca audio out into a analog capture card.

---

