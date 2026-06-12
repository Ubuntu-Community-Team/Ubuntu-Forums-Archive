---
title: "Dvico Fusion PCI card experience survey"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by jimbob on 2007-05-10
I'm about to purchase a Dvico Fusion HDTV5-RT Lite PCI card for my desktop and would appreciate hearing from anyone who has experience with setting up and using this particular card.

This card will apparently pick up anything that the current US broadcast system puts over the air and/or cable (NTSC, ATSC, and QAM).

I do not plan to purchase the remote control opting instead to use my keyboard/mouse for control.
From scanning the forums it appears that Kaffeine will do the job for me.  If I need to record to DVD  I believe I could go the MythTV route.

Thanks for any replies.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by newlinux on 2007-05-10
I have the exact version Dvico Fusion 5 RT Lite in one of my mythbackends and it works well for QAM/ATSC and NTSC. I have it setup as a QAM/NTSC tuner, and I believe I only had to load the cx88-dvb module to get the digital side to work and then it worked fine (analog worked out of the box with tvtime). For the analog side, in myth using V4L drivers I had to jumper audio out from the card to the AUX input on my mobo onboard sound, then find and unmute that input in ALSA. Ended up playing a bit with mythtv sound settings to get good analog sound. Didn't need to do this for digital sound.

I only have one complaint and this is probably myth specific - but when watching live tv in myth and switching from digital to analog, the picture freezes after a second, and I have to change to another analog station before changing before it works properly. Minor annoyance, and since I don't use this to watch live tv much, not really an issue. I don't have this problem when using the card in windows XP (it's on a dual boot system) with the provided fusionHDTV software. 

Overall, I'm happy with the card in my mythtv system. Haven't used it with kaffeine. Didn't get the remote either...

I've  used this card, Kworld ATSC 110s, pchdtv 5500 (which are all ATSC/QAM/NTSC) and an avermedia A180 (QAM/ATSC only). I prefer the Kworld and Avermedia due to the prices I got them for, but the Dvico was the easiest to set up. Picture quality was equal for me with all of them, and it was the only one of these cards that did QAM in windows as well (and that's why it's in my dual boot).

---

### Post by jimbob on 2007-05-11
Thanks for the reply and all the useful information.  Is the video quality as good as it is when I play a DVD?  I have a 24" wide-screen monitor and with DVD's it leaves a black line approx. 1 inch  at the top and bottom of my screen.  I guess this is because the monitor is 1920x1200 and the DVD is  1920x1080i right?  DVD's do look real good however.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by newlinux on 2007-05-11
The picture quality of the HDTV channels should be better than your DVDs, especially with your monitor resoluton. The picture quality of the digital SDTV channels should be about as good as DVDs on your monitor. The analog stations will probably look worse, but it depends on the signal quality in your area.

Yes, the black bars you get are probably due to your resolution. Regular DVDs are actually 480P (720x480) so your video card is upscaling the dvds to get closer to your monitor's resolution (but the ratio is off). DVDs probably look better on your monitor than they do on a regular non-HDTV set. Since televisions currently transmit HDTV at 720p (1280x720) or 1080i they should look better than DVDs on your monitor, especially since your monitor and video card support such high resolutions. Perhaps Kaffeine can stretch the picture or you can play with the resolution settings to get the picture to fill the screen, if you want. For the HDTVs connected to my mythfrontends I have the resolutions set so that HDTV fills the screen, and I usually stretch SDTV content to fill the screen.


The digital signals will come in at pretty much perfect quality (the same as they broadcast it/cable company sends it). How good they look will depend on your video card, monitor, and processor (the combination of your video card and processor need to be powerful enough to properly decode HDTV without dropping frames).

Hope this info helps.

---

