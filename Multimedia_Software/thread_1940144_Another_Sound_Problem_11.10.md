---
title: "Another Sound Problem 11.10"
date: 2012-03-13
forum: Multimedia Software
---

### Post by Andysoldier on 2012-03-13
OK i have of course seen many threads on this but i have tried all of the suggestions, gone through the "comprehensive guide..." *and *because of what has happened i believe someone may be able to help and therefore help many others.
 
My PC is connected via HDMI to a TV. If i hook up my headphones to the back of the PC i hear everything. If i take them out i only hear the sound from games (Eternal Lands and Glest).
 
So, those games must be activating/loading the correct sound driver right? I've looked for any hints of what they are loading in config files etc but can't find anything.
 
Grateful for any help.
 
Ubuntu 11.10 64 bit.
Radeon 6300 on board graphics.

---

### Post by Andysoldier on 2012-03-13
Ok i have more information.  I have sound in Banshee and VLC Media player.

So it appears that it is just Firefox and the O/S sounds i'm not getting through HDMI.

Any help would be appreciated.

---

### Post by Andysoldier on 2012-03-14
Someone suggested trying a different browser so i installed Chromium, still the same unfortunately.

---

### Post by Andysoldier on 2012-03-14
Ok the latest update is that i have tried the Epiphany web browser and i have sound within the browser through my TV.

Unfortunately BBC iPlayer doesn't support Epiphany, and i'm sure plenty of other websites won't.

Can anybody help?  Surely if i find out which driver Epiphany loads then i can somehow make sure that Firefox uses that same sound driver?

---

### Post by BicyclerBoy on 2012-03-14
None of the programs load audio drivers, they possibly output to different devices with different formats.

This on-board graphics is AMD zacate/fusion A E CPU/GPU ?
Are you using AMD catalyst driver?
The open source radeon driver has limited HDMI audio support.
The AMD/ATI model numbering/labelling is almost beyond belief..

What do you get in:
pavucontrol

Can you set your default audio to be hdmi output ?
Firefox just uses the system-wide default audio device with pulse..

dmseg | grep HDA

---

### Post by Andysoldier on 2012-03-14
Thanks for your suggestions Bicycler.

It is one of the Fusion ones i believe - the CPU is the E-300 dual core.

But i have good news.  Someone gave me the solution, which was:

File:
[FONT=Courier New]/etc/asound.conf

[/FONT] Content:
     Code:

     pcm.pulse {
    type pulse 
    } 
    ctl.pulse {
    type pulse 
    } 
    pcm.!default {
    type pulse 
    }
    ctl.!default {
    type pulse
    } 


Thanks again!

I just want to add yes, i am using the Catalyst driver.

---

### Post by BicyclerBoy on 2012-03-14
That makes a pulse plug for alsa.

That is only useful for applications that can only talk to alsa directly.
I don't see this as a proper solution..

All your apps/programs will talk pulse.
VLC can talk directly to pulse or alsa etc.

---

### Post by Andysoldier on 2012-03-15
I'm not sure why it isn't a solution Bicycler?  Could you explain more please?

At the moment sound is working on everything, even after reboots, including VLC and Firefox web browser.

Thanks.

---

