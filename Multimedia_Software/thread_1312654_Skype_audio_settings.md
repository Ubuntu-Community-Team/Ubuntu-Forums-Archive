---
title: "Skype audio settings"
date: 2009-11-03
forum: Multimedia Software
---

### Post by Andyc709292 on 2009-11-03
Odd one for me...
if I install and run skype on Kubuntu 9.10, i get default audio of pulseaudio and I can't be heard.
However if I sudo skype I get capture device as 'default' and all is good.

Should point out that I've come to the end of a tortuous trail of getting flash sound to work by removing any oss related drivers - and that works. Otherwise pretty standard and clean installation.

Any ideas on how to get the sudo settings across to a user? seems odd to me for sure.

Cheers
AndyC

---

### Post by Mikeoak on 2009-11-03
I have noticed that on Skype, if my voice isn't picked on the test call, I need to go to System>Preferences>Sound and click the Imput tab and select my webcam which has a built in mic.  Then it works fine.

---

### Post by Andyc709292 on 2009-11-03
I'd love to - but it's locked at pulsaudio (local server) - can't change it unless I sudo run it from a terminal.
And then it's fine (is default audio in settings) and I can change it anyhow!

---

### Post by Mikeoak on 2009-11-03
Changing the imput device will not change the pulseaudio setting within Skype.  My computer shows two imput devices; does yours just show one?

---

### Post by Andyc709292 on 2009-11-03
Yup.
Looking at it now and it's "PulseAudio server (local)" for mic, speakers and ringing.

And no mic. I can't change it to anything else either.

Doing sudo skype I get:
Mic - Default Device (default)
Speakers - SB Live! Platinum (CT4760P0, ADC Capture/Standard PCM Playback Default Audio...
Ringing - SB Live! Platinum (CT4760P0, ADC Capture/Standard PCM Playback Default Audio...

And the joy of my mother in the UK being able to hear me...
And, bonus, I can change the settings too, just like older skype version (I downloaded it about two days ago and I think it's a new version).

Other info - I had a mare getting Flash audio working - so removed anything oss. That all works now. And if I couldn't get my Skype to work I'd assume that I'd broken my sound drivers. But going in as sudo makes the whole thing work.

Ho hum.

---

### Post by Rumpty on 2009-11-03
Or you can open pulse audio volume control, go to the Input devices tab, and select your mic there. 

Leave pavolcontrol open, start your Skype call, then go to the Recording tab in pavolcontrol, select All Streams, and select Skype

---

### Post by Andyc709292 on 2009-11-04
errr Pulse Audio control.... ???
and pavolcontrol - nope not got that either.

Probably missing something here, but it does seem very complicated given that sudo'ing the app and all is good - I think I'll leave it at that for now and assume it's a skype version issue.

Mind, I'm keen to learn so if there is a way forward then I'll happily try that. 

Cheers

---

### Post by Andyc709292 on 2009-11-04
An update - of sorts...
Just been over to the Skype community forums.
Not a bunch of happy campers over there I can tell you.

I think I'll keep my head down and wait and see what happens (lynching is on the cards I reckon). At least I don't pay for skype!

Anyway, I have a workaround, which after reading some of the threads there I'm happy to have.

(I also have a Vista Laptop - sshhh - which skypes perfectly so my Mum is happy too!).

Cheers

---

### Post by Mikeoak on 2009-11-04
> **Andyc709292 said:**
> errr Pulse Audio control.... ???
and pavolcontrol - nope not got that either.

Probably missing something here, but it does seem very complicated given that sudo'ing the app and all is good - I think I'll leave it at that for now and assume it's a skype version issue.

Mind, I'm keen to learn so if there is a way forward then I'll happily try that. 

Cheers

I think Rumpty was referring to the same audio settings window which you can get to by right clicking on the speaker icon>preferences, although he lost me too when he mentioned the recording tab, since there is no such tab on my system.  Out of interest, you might click on the hardware tab to see if your computer has correctly identified your mic.

I am no expert here, but it seems to me that since you can run Skype using sudo and not as a regular user, that it is a permissions issue.

---

### Post by Rumpty on 2009-11-04
To do any serious setting up of Pulse Audio, you need to have some extra pulse audio stuff installed. Install padevchooser. This will give you various pulse audio GUIs, pa volume control etc., which makes the setting up I mentioned above possible.

---

### Post by Rumpty on 2009-11-04
> **Mikeoak said:**
> I think Rumpty was referring to the same audio settings window which you can get to by right clicking on the speaker icon>preferences, although he lost me too when he mentioned the recording tab, since there is no such tab on my system.  Out of interest, you might click on the hardware tab to see if your computer has correctly identified your mic.

I am no expert here, but it seems to me that since you can run Skype using sudo and not as a regular user, that it is a permissions issue.

Mikeoak, you will see the Recording tab, plus others, when Pulse Audio Volume Control GUI is opened.

---

