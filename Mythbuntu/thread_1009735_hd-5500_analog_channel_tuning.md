---
title: "hd-5500 analog channel tuning"
date: 2008-12-12
forum: Mythbuntu
---

### Post by rbsrao79 on 2008-12-12
Hi,
   I've managed to setup my hd-5500 card on my desktop (mythbuntu-8.10, amd64 3200+ , a8n-vm-csm mb). I have a direct comcast line (and not through a digital box) as my input.

    I have been able to setup my digital channels sucessfully. For analog I have done the following 
1. Setup a v4l capture card
2. setup a v4l->->Television->schedules direct mapping
3. Scan for channels. mythtv locks on to about 78 channels 
4. However when I view the same channels in live tv (I switch to analog mode), I see nothing but noise. Not even a semblance of a picture. I get a noisy audio too. 

What have I missed? I have checked the cable itself. I can view analog channels on my tv quite well.

I understand that this card doesn't do analog quite well, but I imagine it must show me something. 

Much thankings in advance. 

Reevs

---

### Post by ian dobson on 2008-12-13
Hi,

Are you sure the hd-5500 is a  v4l card and not a dvb card, have a look here [http://www.mythtv.org/wiki/index.php/PcHDTV_HD-5500](http://www.mythtv.org/wiki/index.php/PcHDTV_HD-5500).

Regards
Ian Dobson

---

### Post by rbsrao79 on 2008-12-13
Well, from what I've read in various forums and documentatiom, hd-5500 is built as two cards in one. (one digitial and analog. So essentially, I also have a dvb input created (which is how I get my unencrypted digital channels.

In prior versions of mythbuntu, there used to be an "analog" option in the dvb setup screen. However with the current (8.10) I believe that has changed (from what I've been told -- this may be inaccurate) and the hd-5500 has to be configured as if there were two cards in the system (one digital and other analog). 

That said, the "two devices" cannot be used simultaneously. There is an "on-demand" switch in the recording options of the dvb-capture settings that needs to be switched on. 

Rajeev

---

### Post by rbsrao79 on 2008-12-13
Ok. got the ntsc/analog tuner working kind of. After a little bit of hunting I found a switch inside the dvb capture->recording options 

use dvb card for active eit scan (this was on -- I switched it off). This setting causes the dvb part of the card to be constantly in use (hence the analog did not work). 

However, now that I get a picture, its very jumpy (I also get audio)? Any recommendations to improve this ?

Rajeev

---

### Post by joonyah on 2009-05-19
Rajeev,

I was wondering how your analog tuning worked out. 

I just put together a new setup with two pchdtv hd-5500's also using comcast cable as the input directly into the cards. Digital channels were easy to setup, but the analog channels were a little trickier. 

With the two cards I have set up 4 captures cards, two DVB and two V4L. The problem is the sound quality on the analog channels. I've been looking around to see if anyone has any fixes for the sound quality, or if I just have to live with it. 

-- jon

---

### Post by klc5555 on 2009-05-19
> **joonyah said:**
> Rajeev,

I was wondering how your analog tuning worked out. 

I just put together a new setup with two pchdtv hd-5500's also using comcast cable as the input directly into the cards. Digital channels were easy to setup, but the analog channels were a little trickier. 

With the two cards I have set up 4 captures cards, two DVB and two V4L. The problem is the sound quality on the analog channels. I've been looking around to see if anyone has any fixes for the sound quality, or if I just have to live with it. 

-- jon

You need to set the audio capture rate to 48K everywhere from its default of 32K, which default does not work well with this card. 

The sampling rate will need to be set to 48K both in the backend setup under the individual cards, and in the frontend setup under recording profiles, for each resolution (Default, High Quality, etc. listed for the card type.) General list of Recording Profile settings are here: [http://www.mythtv.org/wiki/Recording_Parameters](http://www.mythtv.org/wiki/Recording_Parameters)

See also the general wiki page on the 5500 here: [http://www.mythtv.org/wiki/PcHDTV_HD-5500](http://www.mythtv.org/wiki/PcHDTV_HD-5500)

Cheers! :)

---

