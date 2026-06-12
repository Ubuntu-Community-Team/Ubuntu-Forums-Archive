---
title: "Meter Strength"
date: 2013-01-02
forum: Mythbuntu
---

### Post by neutron68 on 2013-01-02
I'm also trying to get the OSD signal strength and neither ALT-F7 or F7 work.  
I'm currently running Mythbuntu 11.04 and a HD Homerun tuner.

The last time I recall it working was with Mythtv 0.20.2 back in 2008 with a pchdtv HD-3000 pci tuner card.
Back then I was using Knoppmyth R5F27.

Can someone confirm when the OSD signal meter was removed from Mythtv?

Thanks,
Eric

---

### Post by AlecJ on 2013-01-03
If You have the long and latitude of the Transmitter site and a GPS at home,
you can plot the course on Google maps or alike to get a bearing in Deg's then use a compass to aim your antenna.
It's not like a Satellite Dish you don't need to worry about inclination or disinclination just sit the main pole at right angles using a sprite level so it's straight.

For best results use an amplifier.
I used to use a 6 way amp with coax patch leads into each tuner on my Mythbox.
The Amp also helps protect the tuner cards from lighting damage.

---

### Post by neutron68 on 2013-01-04
> **AlecJ said:**
> If You have the long and latitude of the Transmitter site and a GPS at home,
you can plot the course on Google maps or alike to get a bearing in Deg's then use a compass to aim your antenna.
It's not like a Satellite Dish you don't need to worry about inclination or disinclination just sit the main pole at right angles using a sprite level so it's straight.

For best results use an amplifier.
I used to use a 6 way amp with coax patch leads into each tuner on my Mythbox.
The Amp also helps protect the tuner cards from lighting damage.
Was your answer intended to answer my question?
I asked of someone can confirm when the OSD signal meter was removed from Mythtv?

Eric

---

### Post by AlecJ on 2013-01-04
Yes sorry it not their in .26

---

### Post by topcat5 on 2013-01-06
If you are using a hdhomerun, just run their config utility directly.  (can be used remotely on a wireless laptop, great for antenna aiming)

If you are using a DVB device you will need to load the tools suggested above and use them for pointing.       

You really want to look at _"signal quality"_ when aiming an antenna, not "signal strength".  The hdhomerun utility will show this.  I'm not sure about the DVB tools.

---

### Post by nickrout on 2013-01-06
hdhomerun have an excellent andoid app for this too. Much easier carrying your cellphone on the roof than your laptop...

---

### Post by neutron68 on 2013-01-09
I am asking on behalf of a friend of mine that I am helping to configure Mythbuntu 12.04.  He has a pchdtv HD-5500 tuner card.

Mythbuntu 12.04 has MythTV 0.25 (not 0.26) rolled into it.

Does 0.25 have the OSD signal meter removed?

Thanks.

---

### Post by thaibuntu on 2013-02-05
The OSD Signal Strength is there, but it may have the same hot-key combo as the window manager for moving windows. This was the case for me in LXDE (the is what mythbuntu uses as the default desktop, right?).

By changing the key combo in the settings, I was able to bring up the signal strength meter. HOWEVER, this may or may not actually give you signal strength. For me and my HVR-2250, while watching live tv, the OSD signal strength meter would report 0%, 0 SNR and black out the screen. I believe this is a lack of functionality in the driver/firmware. Doing a test with the "femon" command line tool will give you an idea of whether or not your tv tuner card can report signal strength.

---

### Post by neutron68 on 2013-02-05
> **thaibuntu said:**
> The OSD Signal Strength is there, but it may have the same hot-key combo as the window manager for moving windows. This was the case for me in LXDE (the is what mythbuntu uses as the default desktop, right?).

By changing the key combo in the settings, I was able to bring up the signal strength meter. HOWEVER, this may or may not actually give you signal strength. For me and my HVR-2250, while watching live tv, the OSD signal strength meter would report 0%, 0 SNR and black out the screen. I believe this is a lack of functionality in the driver/firmware. Doing a test with the "femon" command line tool will give you an idea of whether or not your tv tuner card can report signal strength.
So what was the OSD key combo by default, and what did you change it to?  And, where did you change it?

This Femon?
[http://linuxtv.org/vdrwiki/index.php/Femon-plugin](http://linuxtv.org/vdrwiki/index.php/Femon-plugin)

Can this be installed from the Ubuntu Software Center (Synaptic Software Center)?

Eric

---

### Post by PhilWig on 2013-02-05
It's in the key bindings.

Frontend > setup > edit keys > TV playback > signalmon

On my 0.25 setup it's set to ALT + F7 but that does not bring up a signal strength meter.  Nor does '$' if I insert that as an alternative.
Doesn't take you any further forward I'm afraid, but I have found by accident 'text' (F7)  and 'red button' (F2) for selecting news, weather etc which was a personal quest.

Phil

PS not tried it myself but have you seen this?
[http://www.linuxtv.org/wiki/index.php/Zap](http://www.linuxtv.org/wiki/index.php/Zap)

---

### Post by wildmanne39 on 2013-02-05
*Thread moved to **Mythbuntu**.*, If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

### Post by thaibuntu on 2013-02-05
Yes, the default key combo is Alt+F7, which is also the default for "move window" in lxde. I confirmed this by opening a browser window and hitting Alt+F7, which changes the mouse pointer to a hand grabbing the title bar of the window.

Changing the key combo to Shift+F7 in mythfrontend allowed me to bring up sigmon.

There are two options for looking at signal strength, other than the osd. One is Femon and the other is tzap (or azap for atsc). I have not tried the femon-plugin, I'll give that a look. I did try azap, but couldn't figure out the syntax for setting a scan of individual channels when I don't know the channel string.

---

### Post by topcat5 on 2013-02-06
It seems to me that I tried to get it to work on 0.25 by binding it to one of my keys on my remote.  When I tried to use it, during live TV it tended to hang the FE, so I removed it.  This was with a HDHomeRun Dual tuner.   

On the plus side however the HDhomerun has a set of command line options to get statistics for any tuned channel.  And you can do this remotely from another PC that would be easier to use than typically on the FE itself.   You will need to install the HDhomerun software on whatever PC you wish to do this on.

If you are doing this to correct reception issues, you will want to look at signal quality rather than signal strength.

---

### Post by nickrout on 2013-02-06
There is also a great android app to show tuning info. Nice and portable for getting on the roof and adjusting the antenna.

---

