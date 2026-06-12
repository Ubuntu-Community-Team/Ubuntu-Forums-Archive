---
title: "Concerning input volume control......"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by ElEdwards on 2007-06-14
I'm a relatively new Ubuntu user and am really enjoying what I've learned so far. :)  Presently, I'm in a dual boot configuration with WinXP....but I want to sever the M$ cord. ;)

Here's my issue.... I am a commercial voice-over announcer and for a long time have used Adobe Audition in WinXP on my laptop to make my recordings with a mic plugged directly into the Mic-In on the laptop.  In Windows, there are separate controls for input levels and output levels.... but I can't seem to find an input level control(s) in Ubuntu, so my mic level in Ubuntu, even with 20+ boost on, is about 25% of the level I can achieve in Windows.

I have Alsa installed (I updated to UbuntuStudio yesterday) and have tried Audacity and a few other programs, too....but the mic level is far too low. :(

Hopefully, this is nothing more than me having a DUH! moment.... but how can I change the input level from my mic?

In case you need to know, my laptop is a Presario 2170us with a Conexant audio card built in.

Thanks! :)

---

### Post by dabl on 2007-06-14
Yes, the audio input level controls are less than obvious in Ubuntu, but you should be able to get it just right. I'm away from Ubuntu at the moment, so this is going to be a little vague.  Right-click on the little speaker icon in the upper right corner of your desktop, then you need to choose something like "open mixer" or "preferences", and then you are going to look for a way to "edit preferences".  Play around with it long enough and you'll get to a panel that has a tab for "Inputs", and on that will be some sliders with faux "mute" lights that you need to make sure are unmuted.  On mine, the "mux" slider needs to be all the way to the bottom,and the "PCM" slider needs to be about midway.

Use Audacity to do test recordings, and watch the level that way while you fiddle with the settings in the mixer.

HTH!  :)

---

### Post by dabl on 2007-06-14
OK, got the definitive answer, with screenshot.  Right-click the speaker icon, select "Open Volume Control", then on that panel click on the "Recording" tab, and then set it something like you see in the screenshot -- that is where mine is set to capture from "Line In", from my amplifier.  Make sure the "Switches" tab does not have a checkmark in "Line in as output" -- mine needs the other option checked. On the top menu bar (of the same volume control panel), choose "Edit" and "preferences" (your only choice) make sure there is a checkmark in _every_ box (I know, one of them says "Line in as Output" ... I'm just telling you how I got happy with my recording setup, not whether it makes total sense).

Also after right-clicking the icon, select "Preferences" and make sure it is set to "ALSA Mixer".  I hope this helps!

---

### Post by ElEdwards on 2007-06-14
Well, dabl, between your help and my fiddling, I finally got it! :)

I failed to mention that I recently updated to UbuntuStudio...... and in Applications/Sound & Video/ is an app named QAMix, which is a mixer for ALSA.  I was finally able to get the mic level up to something that peaks at 100%....and I'm a happy camper!! :D

Thanks!

---

### Post by dabl on 2007-06-15
Yay -- good job!  :guitar:

---

