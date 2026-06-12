---
title: "all dvd ripping apps constantly crash during rip"
date: 2009-04-12
forum: Multimedia Software
---

### Post by eival on 2009-04-12
hello all, im trying to rip some standard commercial dvd's(nonHD-BluRay) and so i downloaded the top 4-5 ripping apps from the package manager(Acid Rip, DVDrip, K9, and one other)

all of them can read the dvd(name/title/chapters), they all give me a choice of which chapters i want to rip with no issues.

the only issue is when i actually start the ripping process, most of them run for about 20 seconds then the apps crash without warning.

i tried different variations of file types and settings in all 4 of the DVD ripping apps, AcidDVD Rip is the only one that stays running, but the only message under DeBug is "player stopped by user" which isnt the case cause i dont click anything after i click Start.

i then wind up with a saved file thats incomplete, when i play the file through VLC i get the error pop up that "the AVI is damaged do you want to try and repair" and after the attempted repair it plays the 20 seconds that were saved but only the audio, not the video.

now one app simply called DVD::Rip
has a system check under the preferences and all of them are GREEN/OKAY except this one line found in the COMMANDS tab

"STDIN player command: xine not found : NOT Ok"

so i first assumed this is a video codec that i needed to install so i search the packages for xine, but it comes back with a bunch of media players which i already have the Movie Player(GStreamer) installed, so i tried installing the Movie Player Totem(xine backend) for the hell of it, but nothing changed

so now im stuck with no clue what the real issue is and how to fix it.

---

### Post by wolfen69 on 2009-04-12
you might want to install more codecs. search synaptic for **gstreamer bad** and **gstreamer ugly**. also, **win32 codecs**. but you might need to install the medibuntu repos first. did you also install **libdvdcss2**?
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

---

