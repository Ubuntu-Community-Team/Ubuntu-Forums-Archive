---
title: "No sound when plugged HDMI cable."
date: 2013-09-19
forum: Multimedia Software
---

### Post by Edgar_Sarmento_Bezerra on 2013-09-19
Hi. :)
I'm a newbie and a Ubuntu 12.04 user.
I've tried to solve the problem but I couldn't do it. 
My ALSA information is located there: [http://www.alsa-project.org/db/?f=ffa30916bb0b5ca6973c61f798748303ae35b0c4](http://www.alsa-project.org/db/?f=ffa30916bb0b5ca6973c61f798748303ae35b0c4)
When I go to System Settings>Additional Drivers that's what appears written: "No proprietary drivers are in use on this system."
                                        
Well, hope you help me. Thanks.

---

### Post by perspectoff on 2013-09-21
I use Pulse Audio, and for HDMI I do this:

[http://ubuntuguide.org/wiki/Ubuntu_Raring_Hardware#HDMI_with_PulseAudio](http://ubuntuguide.org/wiki/Ubuntu_Raring_Hardware#HDMI_with_PulseAudio)

In brief, I made sure that PAVU Control was installed (PulseAudioVolume):

 sudo apt-get install pavucontrol

The I start PAVU Control and make sure Pulse Audio has HDMI designated:

PAVU Control -> Multimedia -> PulseAudio Volume Control -> Configuration -> Internal Audio -> Digital Stereo (HDMI) Output 

There was a small quirk on my system: The HDMI cable had to already be plugged in at the time I changed the PAVU Control settings (or was it at bootup? -- I can't remember at the moment).

Then everything works ok for me. I have to switch it back if I later want to pipe the audio back through my analog (ALSA) card.

---

### Post by Edgar_Sarmento_Bezerra on 2013-09-26
> **perspectoff said:**
> I use Pulse Audio, and for HDMI I do this:

[http://ubuntuguide.org/wiki/Ubuntu_Raring_Hardware#HDMI_with_PulseAudio](http://ubuntuguide.org/wiki/Ubuntu_Raring_Hardware#HDMI_with_PulseAudio)

In brief, I made sure that PAVU Control was installed (PulseAudioVolume):

 sudo apt-get install pavucontrol

The I start PAVU Control and make sure Pulse Audio has HDMI designated:

PAVU Control -> Multimedia -> PulseAudio Volume Control -> Configuration -> Internal Audio -> Digital Stereo (HDMI) Output 

There was a small quirk on my system: The HDMI cable had to already be plugged in at the time I changed the PAVU Control settings (or was it at bootup? -- I can't remember at the moment).

Then everything works ok for me. I have to switch it back if I later want to pipe the audio back through my analog (ALSA) card.

Perspectoff, I've followed each steps you said and yeah the sound has worked (I've plugged in the HDMI cable then I've changed the *PAVU Control settings* therefore I haven't plugged it in at boot up) however after watching the video I've wanted I've plugged off the HDMI cable and after that I've switched back the *PAVU Control settings* from *Digital Stereo (HDMI) Output + Analog Stereo Input* to *Analog Stereo Input* however now I have no sound neither in pc nor when I plug in the HDMI cable.
I've tried to change the *PAVU Control settings* to *Analog Stereo Output* as it is taught there [http://ubuntuguide.org/wiki/Ubuntu_Raring_Hardware#HDMI_with_PulseAudio ]("http://ubuntuguide.org/wiki/Ubuntu_Raring_Hardware#HDMI_with_PulseAudio")but the sound hasn't returned. 
At *System Settings>Sound>Output*, between the options *Dummy Output *and *Speakers Built-in Audio* in the box *Play sound through* is selected _Dummy Output_.
At the *PAVU Control settings>Playback* in *System Sounds Mono* it is on _Silence_.
I hope this informations could help.
What should I do? :(

---

### Post by Edgar_Sarmento_Bezerra on 2013-09-26
Perspectoff, I've solved the problem. :p
I've restarted the pc with the HDMI cable plugged in then I've opened and switched the PAVU Control settings at Configurations from Analog Stereo Output to Digital Stereo (HDMI) Output and it's worked. 
Before plugging off the HDMI cable I've switched back to Analog Stereo Output then I've had the sound back.
Thank you for all your help. God bless.

---

