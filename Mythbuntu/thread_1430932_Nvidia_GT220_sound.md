---
title: "Nvidia GT220 sound?"
date: 2010-03-16
forum: Mythbuntu
---

### Post by xinix on 2010-03-16
Does anyone have sound working with an Nvidia card that has built in sound?  I'm not sure the drivers are there for linux but I thought I'd ask and see.  

I have a GT220 that has native sound for HDMI.  Sound from this card doesn't work for me in Ubuntu but every so often I have to boot windows <rant>stupid ITS requires you to run a little program to get online each month; the linux version doesn't work</rant> and today I was greeted by sound coming from my TV.  I was very surprised by this, I have the TV connected to a DVI->HDMI cable so I didn't think there would be sound at all.

It never occurred to me to try to get sound from a DVI port so I never looked into getting the sound working on the card.  Has anyone gotten this to work?

---

### Post by scudderwagg on 2010-03-16
Check out this HOW TO from the XBMC folks.  I followed it and got HDMI audio to work on my GT220.  Check the thread at the XBMC forums this page references as things are changing quickly on this.
[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240)

It appears the site may be down due to technical difficulties.  Here's a cached version if you're impatient.
[http://74.125.93.132/search?q=cache:I_DL6jiZVbMJ:wiki.xbmc.org/%3Ftitle%3DHOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%252C_GT220%252C_or_GT240+HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%252C_GT220%252C_or_GT240](http://74.125.93.132/search?q=cache:I_DL6jiZVbMJ:wiki.xbmc.org/%3Ftitle%3DHOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%252C_GT220%252C_or_GT240+HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%252C_GT220%252C_or_GT240)

Basically you have to download the most recent ALSA drivers, grab a snapshot of the bleeding edge stuff then patch that for the GT220.  You also have to make sure you have very recent Nvidia drivers (at least 190) before you do anything with ALSA.

---

### Post by David Grigor on 2010-03-16
I was able to get it working a few weeks ago using the above notes.

Two parts of a little confusing:

When downloading the patch has a funny name and wasn't sure it was the right file. I renamed it to what the notes are looking for and went well. 

Modifying the /etc/modprobe.d/sound.conf was a bit confusing as well. To make it easier, I disabled all the motherboard sound in the bios so only the gt220 audio devices would show up instead of trying to figure out what the addresses should be.

---

