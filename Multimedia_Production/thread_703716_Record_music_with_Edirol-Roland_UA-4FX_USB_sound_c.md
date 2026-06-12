---
title: "Record music with Edirol-Roland UA-4FX USB sound card??"
date: 2008-02-21
forum: Multimedia Production
---

### Post by patagonik on 2008-02-21
Hi there!

I'd like to know if someone out there has ever used the Edirold UA-4FX sound-card to record music, specifically using Ardour2 (or other software..)

I need a USB sound-card working in Linux (Ubuntu) to record music (mics, drums, etc..) so if anyone there knows about a suitable one, please let me know. I've been already around the Compatible Hardware pages of Ubuntu and ALSA, and there are tons of them, so that's what i need to hear about someone who had already experimented with them.

Thanks you all!

---

### Post by dingo on 2008-02-21
I have used the Edirol UA-25 with Ubuntu (Dapper to Fiesty) and it works great. No drivers to install (it's recognized when I plug it in). I'm using it mainly with Audacity and Ecasound running it through the alsa interface.

There's more info on using the UA-25 under linux here:

[http://alsa.opensrc.org/index.php/Edirol_UA-25](http://alsa.opensrc.org/index.php/Edirol_UA-25)

Overall, I have no complaints, but then again, I'm not a very demanding user. I just want it to record without clicks and pops, and playback through a cheap stereo.

Good luck

---

### Post by patagonik on 2008-02-22
Great! Huge help!!!

Could you tell me what are you actually recording? Voice, drums, keyboards, guitars...? Could you link something you've recorded? 

Is that a problem to have just a USB connector, and not a USB 2.0 connector? Do you think that the UA-4FX would be supported as well? I think that it might be, but i'd like to confirm... 

Dude, you gave me enormous good news! Thanks a lot!!

---

### Post by dingo on 2008-02-22
I record mostly acoustic stuff using microphones (ATM-35 and an SM-58 ). The ATM-35 is a clip-on condensor mic so I sometimes use the phantom power feature of the UA-25. Mostly I record accordion, mandolin, and bouzouki.

As for the USB connector, I don't really think it matters if you have USB 2.0 or not (at least at 44.1K or 48K sample rates...I never tried 96K). I used the UA-25 with 3 different laptops (only one of which had USB 2.0). I couldn't tell much difference.

As for the UA-4FX...I don't have any idea. 

Mostly, now, I use the UA-25 as an output soundcard to interface a laptop to my stereo. I bought a Zoom H2 which covers most of my recording needs, and I'd rather spend the time playing, than setting up microphones.

All-in-all though, I'm very happy with the UA-25.

---

### Post by m.letcher on 2008-03-23
I have the same question about getting Ubuntu recognizing the external UA-4FX box for midi in/out. I also use it as a second sound card and feed the internal Realtek card out through an external mixer to drive the stereo rig via the UA-4FX. My midi gear audio also routes into the mixer then the UA-4FX where the PC can record it directly via the USB. I'm not that familar with ALSA so it may not be too difficult. I also have a MOTU/USB micro-lite multi-port midi router that I'd like to drive as well since thats what I direct the sequencers out to to drive the external synths.

Sorry that this isn't an answer but rather a follow up question.

---

### Post by robeast on 2008-03-24
[http://www.alsa-project.org](http://www.alsa-project.org) lists all of the Edirol UA series as supported EXCEPT for the 4fx. It also doesn't list the 4fx as UNSUPPORTED, so you could be a dear and test it out! If it happens to work it's one more device to add to the compatible list.

Check out the second link in my sig for a concise list of known, compatible devices.

---

### Post by m.letcher on 2008-04-04
Audio appears OK, though apparently the mode switch on the box itself needs to be in 'normal' ( not 'advanced' ) and power cycled. This is reported to disable the midi, but didn't for Vista. I don't have it getting recognized as a midi device yet. I saw some discussion that Gutsy snd-usb-audio has issues with 'slow' USB1.1 interfaces but that these are addressed with Hardy so I'll wait for release later this month.

"Supported" is kind of an open call for me to date, until I play with the audio somemore.There is a nice ALSA wiki page for the UA-4FX with suggestions for advanced mode.

I don't expect to find any help with a MOTU micro-lite ( USB to Midi IO ) box though it drives my sound modules. Too bad for MOTU, since I really like the UbuntuStudioAudio package and will probably finally shift from Sonar/Acid. I'll probably look for a ALSA compatable VST wrapper and go with my soft synths. 

Thanks for suggestions and recommendations.

---

