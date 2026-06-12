---
title: "Getting Surround 5.1 to work"
date: 2008-07-01
forum: Mythbuntu
---

### Post by countcobolt on 2008-07-01
Hi all,

I have installed MythBuntu a couple of days ago, but am still struggling to get surround to work

I have an old soltek mainboard with an nvidia nforce soundcard

following problems occur:
- speakertest surround51 -c6 only outputs on the front speakers (this is acceptable for the general stereo mp3 etc)
- media-> play music locks when I select alsa:surround51 in the general setup even with downmix selected in the configuration
- I have read up on using dmix62 etc (asoundrc file) yet I am wondering, if I want to use xine and AC3 will I get proper surround then, or just the mixdown (I want the movies to play in full 5.1 surround and music to duplicate)

Any ideas what I can do?

regards
Steve

---

### Post by countcobolt on 2008-07-02
I have tried pulsaudio, yet I can not connect to the server even when it is running... 

This is giving me a big pain...
Anyone?

---

### Post by Trollslayer on 2008-07-02
This is usually down to the driver, search for posts about ALSA.

---

### Post by stevecartermo on 2008-07-04
In alsa mixer you have to disable SOUNDBLASTER setting and then store the settings after you get them working, I can't remember the exact syntax. slsactl store or something

---

### Post by stevecartermo on 2008-07-04
for a soundblaster live,  in alsa mixer you have to disable, SOUNDBLASTER setting, this activates 5.1 sound and then store the settings after you get them working, I can't remember the exact syntax. alsactl store or something

other sound cards have a channel setting in alsamixer that specifies the number of sound channels to use

---

### Post by countcobolt on 2008-07-04
A small update

I managed to get surround working through the hints steve gave. 
I even added an ch51up which reroutes to center/LFE and rl/rr. 
I can use this alsa device without a problem in mplayer and have stereo on all speakers.

The issue I get is when I configure mythtv to use ch51up mythstreams works fine and everything except mythmusic. It is as if it does not play the track and keeps sitting at the same second... :confused:

I first assumed this was a complete error with mythtv, until I found the the other plugins work fine

has anyone seen this before?

kind regards
Steve

---

### Post by Trollslayer on 2008-07-05
> **stevecartermo said:**
> In alsa mixer you have to disable SOUNDBLASTER setting and then store the settings after you get them working, I can't remember the exact syntax. slsactl store or something

How do you disable the Soundblaster setting?

---

### Post by countcobolt on 2008-07-07
Hi all,

to get surround working I just disable all input in the input tab in kmix. I disabled duplicate (in short nothing is lit in the input tab). With the onboard I set up 6 ch and shared

With speaker-test I checked if all the speakers where working. 
I looked on google and made my own ttable in alsa for ch51up and checked with speaker-test again (remember only 2 channels if testing.)
I also changed mplayer to use SDL as a default output for sound and set
SDL_AUDIODRIVER=alsa
SDL_AUDIODEV=ch51up
This seemed to enable all surround or upmix in each application except mythmusic

To solved the mythmusic problem I had to select the old OSS name (/dev/dsp) and that seem to do the trick...

One more thing I need to get up and running is creating a controller device/mixer so I can raise/lower volume in 1 shot with the remote control (now it is only doing the fronts)

A little issue I seem to experience is the fact that sometimes there is not much sound coming out of the rear speakers, yet only now and then some crackling noise (yet this could be the fact of the speakers and not mythtv)

hope this helps someone

---

