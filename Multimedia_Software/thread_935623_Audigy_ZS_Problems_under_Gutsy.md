---
title: "Audigy ZS Problems under Gutsy"
date: 2008-10-01
forum: Multimedia Software
---

### Post by pgmer6809 on 2008-10-01
1. GNUSOUND crashes linux. Have to reboot.

2.GNOME Alsa mixer mostly works. I can see all the devices, mute them, Volume control etc. But when started and when trying to edit the card properties I get:
An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly.

Then Details gives many errors relating to comma in a directory name:
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9750,51-Headphone": `,' is an invalid character in key/directory names

cmd line alsamixer works without giving errors.
Volume control applet works OK too.

3. Sound Recorder application will not start.
Gives error screen:
Your audio capture settings are invalid. Please correct them in the Multimedia settings.

But it does not say where Multimedia settings are. 

4. System=>Preferences=>Sound will open. I can set the playback device to one of several devices. When I click TEST they all work. But there is no Input device setting, only a Capture Device under the audio conferencing section. I can try all 8 possibilities there, but when I click TEST I just get an error that it cannot create the pipeline.

Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

5. Audacity will play but when I try to record all I get is silence.
Record function is working but it does not see any sound, even though I can hear the source going to LINE-IN through my headphones.


Has anyone gotten an AUDIGY ZS to work using Gutsy?
(Heron is out of the question. Too many issues with it other than sound.)

Any help greatly appreciated.

pgmer6809 <at> yahoo dot com

---

