---
title: "Recommended TV Tuners for Ubuntu"
date: 2008-07-08
forum: Multimedia Software
---

### Post by TransplantedCanuck on 2008-07-08
I'm looking to spend under $100 (dollars, less in euros) for a decent enough tv card.  The main thing is: I want to be able to plug it in and have it work, with minimal effort. I've given up on ever getting this Winfast TV2000 working. No matter what I try/do/read/install/uninstall/reinstall, it just won't load properly. 

Are there any GUARANTEED to work cards out there? 

It's going to be displayed on the computer monitor (19 inch LCD), and sound will be over the normal computer sound output (stereo).

Requirements:
- Don't care/want/need HD, surround sound, whatever other fancy TV snobbery people have
- No FM tuner needed (though could be nice)
- Remote would be convenient,but not mandatory.

---

### Post by wolfen69 on 2008-07-08
the Hauppauge PVR line of cards (pvr150, 250, 350, 500) will work perfectly in ubuntu. all that is needed is to do:```
sudo apt-get install ivtv-utils
``` and you are good to go. i use vlc to watch tv and it works great. If you get a Hauppauge card, PM me and i'll tell you how to set it up with vlc. it's ez. btw, i have the PVR150. it's good basic tv tuner.

---

### Post by dentaku65 on 2008-07-08
Hauppauge Wintv Nova T-Stick (usb2 with no remote control) works very good; is a DVB-T (digital terrestrial (?)) usb key, is perfect with **kaffeine** player

---

### Post by piratebill on 2008-07-08
I have the ATI tv wonder VE.  It works perfectly out of the box

---

### Post by darthchaosofrspw on 2008-08-07
> **wolfen69 said:**
> the Hauppauge PVR line of cards (pvr150, 250, 350, 500) will work perfectly in ubuntu. all that is needed is to do:```
sudo apt-get install ivtv-utils
``` and you are good to go. i use vlc to watch tv and it works great. If you get a Hauppauge card, PM me and i'll tell you how to set it up with vlc. it's ez. btw, i have the PVR150. it's good basic tv tuner.

My next card will be a Hauppauge. I'm currently using an AVerTV GO 007 FM Plus on VLC (on Xubuntu Hardy). Picture quality is great, and video recording quality in MPEG-2 mode is great. My tuner card is one of those that plays the audio itself through the comp's sound system (it doesn't have an audio-out jack to play audio through the comp's line-in), so my next card will be a Hauppauge one that plays audio through the line-in jack. I keep VLC on channel 3 so I can just use my VCR as the audio source and as a cable box.

---

### Post by gjhuff on 2008-08-08
I have Hardy Heron installed on a HP ZD7249cl laptop.  I'd like to get my Hauppauge HVR-950 working and have tried numerous threads without success.  Can anyone direct me to an easy (relatively, I know this is Linux) method to get this card working?

---

### Post by steefjeqv on 2008-08-11
A Terratec Cinergy 1400 DVB-T works very good, and should be easy to find in Germany.

Greetings,
Steven

---

### Post by rusted88 on 2009-01-21
> **gjhuff said:**
> I have Hardy Heron installed on a HP ZD7249cl laptop.  I'd like to get my Hauppauge HVR-950 working and have tried numerous threads without success.  Can anyone direct me to an easy (relatively, I know this is Linux) method to get this card working?

I have the same problem i tried like 5 methods and only one worked but only the video, I later found that there was a way to add sound but i couldn't make the video work again.

---

### Post by cmargolin on 2009-01-22
> **gjhuff said:**
> I have Hardy Heron installed on a HP ZD7249cl laptop.  I'd like to get my Hauppauge HVR-950 working and have tried numerous threads without success.  Can anyone direct me to an easy (relatively, I know this is Linux) method to get this card working?

Try [http://www.technetra.com/2008/07/01/over-the-air-digital-tv-with-linux/](http://www.technetra.com/2008/07/01/over-the-air-digital-tv-with-linux/)

---

