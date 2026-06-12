---
title: "Encore fm tv tuner"
date: 2008-10-01
forum: Mandriva/Mageia
---

### Post by Mr Pockets151 on 2008-10-01
I finally got my tvtime to start with my card. 

[LIST]
[*]ENLTV-FM TV TUNER PRO from encore electronics.
[/LIST]This is being detected as  an saa7134 chipset, however it is saa 7130.  I had to upgrade my old graphic card to a "hell-of a way better one," in all respects.  Now-TVTIME runs smooth as pie except- I haven't been able to get sound.  I've tried trouble shooting as much as I could, for an intermediate, MANDRIVA 2008.1  user.  

Steps to take to begining proper trouble shooting, using KDE desktop.  *****UBUNTU TVTIME DOES NOT RUN STILL...PERIOD!**:guitar:

THX.  most other mandriva forums are a bit unorganized.  Like ubuntu forums layout.  :popcorn:  I haven't tried rc 2 out of the box yet....I was actually only on here to burn the rc 2 gnome CD.   THANKS AGAIN!

---

### Post by AdamWill on 2008-10-02
saa cards are the devil's work. Reason being that there's one driver for all seventy zillion tuner and card types, and it doesn't do auto-detection very well. It's 'detected' as a saa7134 simply because the driver is called saa7134 - it's showing the driver name in use, not what chipset it thinks the card has.

Anyway, if you've got a picture, that's usually actually the hard part out of the way.

As far as sound goes, with TV cards, I've always found the old analog method the most reliable. There should be a 3.5mm (standard ipod-style) line-out connector on the back of the card. Get a 3.5mm -> 3.5mm audio cable and plug one end into that and one end into the line-in on your soundcard. Then just set the mixer settings appropriate to play back sound from the line-in port on the card, and that should hopefully be that.

There are kernel drivers and stuff that are supposed to let you get the audio digitally from the TV card to your sound card via the Magic Of Science or smoke signals or some such crap, but I never got them to work. Stick with the cable.

---

### Post by Mr Pockets151 on 2008-10-02
Nice..lol @ smoke signals.  I'm pretty sure that's the way I have the tuner setup for audio.  The mixer settings in MCC?  I'll check when I get home.  Over @ club mandriva forum, some mentioned that I may need the AAC codec installed.  I did a google on that and couldn't put two and two together on that one.

---

### Post by AdamWill on 2008-10-03
That was completely wrong, I think they were just thrown off by the two 'a's in the driver name. :) AAC is a compression codec like MP3, doesn't have anything to do with the current case.

If you've got the audio cable connected, then yep, check the mixer settings.

---

### Post by Mr Pockets151 on 2008-10-03
So I checked I do have the linein/out lead connected.  Also I do get sound but I have to turn the volume on my speaker system all the way to max, and I can hear the "faintest" sound barley. My mixer controls are all maxed out.  I have the tv tuner jack going to my sound card jack.  I wonder if I try going off just the onboard motherboard audio, which would suck because I don't use it.

---

