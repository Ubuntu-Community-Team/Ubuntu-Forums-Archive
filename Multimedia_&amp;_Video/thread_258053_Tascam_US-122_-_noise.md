---
title: "Tascam US-122 - noise"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by hickmann on 2006-09-15
I have properly installed an US-122 and it's working fine (besides the fact that I need to initialize it everytime I start Ubuntu). The problem is: everytime I pause a music, be it in Totem or any other player (Kaffeine, Amarok), an awful noise comes out. Depending on the player, it stops after a few seconds, or only when I unpause the music or close the player. I have no idea of what I can do about this, and couldn't find such a problem in any other thread. Please, anyone have any ideas?
Thank you!

---

### Post by Stochastic on 2006-09-17
I can confirm that, I just installed it via [this Howto]("http://www.ubuntuforums.org/showthread.php?t=194490&highlight=US-122+Tascam") and I get a very loud buzzing noise when pauses occur.

---

### Post by David S on 2006-09-18
I have a similar problem.  I get an annoying buzz for about one second each time a player is stopped (or finished playing).

---

### Post by Stochastic on 2006-09-22
Can anyone explain where this noise is comming from?  Is it the USB drivers?

---

### Post by hickmann on 2006-10-28
Anybody, please??

---

### Post by Stochastic on 2006-11-19
I'd really like to use this soundcard, can anyone suggest a manner in which to troubleshoot the issue?  We'll take anything, throw us a bone.

---

### Post by augied on 2007-07-13
I've got the same problem.  Has anyone figured this out?

---

### Post by jaywalker13 on 2007-07-31
Oops I just posted this as a separate problem. 

I get the sound too, but not on Amarok. Does that tell us anything?

Jay

---

### Post by augied on 2007-07-31
Same here, Amarok works perfectly, but everything else buzzes.

Also, I can't get sound from multiple applications.  I could with my built in sound, but not with the Tascam.

---

### Post by jaywalker13 on 2007-08-01
Audacity doesn't buzz either, but a crackling sound while it is playing files makes it unusable.

Jay

---

### Post by fredj on 2007-08-02
Sounds lke a Tascam problem. Have you looke dfor updated firmware for this device?

---

### Post by jaywalker13 on 2007-08-02
fredj, thanks for the reply.

I have used the latest alsa firmware for the usx2yloader. Is this the same as Tascam firmware. I don't think Tascam does support for Linux - only Windows and Mac.

Jay

---

### Post by fredj on 2007-08-03
You should not be looking for Linux dirvers from Tascam but only for any update to the firmware 
embedded in your Tascam usb sound device. Linux has inbuilt drivers for standard usb sound devices
but it seems like your Tascam isn't behaving in a standard way. However the horrible noise shouldn't
matter too much as long as it doesn't interfere with recordings.

---

### Post by RgnKjnVA on 2007-11-14
Same here and this is the last big issue with my first foray into Ubuntu. As others have noted, Amarok seems to not produce the noise when paused however I do hear the noise briefly when changing playlist items while another is playing (not to mention plenty of Demux error messages unrelated to the US-122).

One thing I've noticed is that the frequency of the noise seems to change based on where in the media file you pause. It's like it's looping a very short section of the media instead of stopping/pausing.

re: firmware updates, I'm not sure what we're supposed to do with these but...
[http://langerland.de/linux/usx2y/](http://langerland.de/linux/usx2y/)

Also this looks promising but I'm stuck at the office so I can't try try it (argh!)
[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

---

### Post by yeehawjared on 2007-11-18
are you all using laptops?  When plugged into the AC I always get buzzing from my integrated sound card and the Tascam... i think.  Try running on battery for a hot second and see if that helps anything.

---

### Post by drewdlephone on 2008-04-04
Nope, on a desktop here, I get the same noise, which is a shame because the D/A converters in the US122 make for some amazing audio playback when coupled with a FLAC library. As noted above, the frequency of the noise changes; I'm of the opinion that pausing the device doesn't mute the sound coming from it, just stops playback on a single frame of the file, and that's what you're hearing, that frame repeated ad finitum. I have no idea how to fix it though. I sure would like a fix.

---

### Post by RgnKjnVA on 2008-04-04
very aggravating issue especially since some media players do not provide a stop function just play/pause. For these, one has to quit the app to stop the media. *sigh*

---

