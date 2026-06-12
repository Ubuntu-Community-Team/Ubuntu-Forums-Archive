---
title: "No recording no sound Audacity"
date: 2008-10-31
forum: Multimedia Software
---

### Post by Spaceman9 on 2008-10-31
I've tried every alsa and oss setting and Audacity won't record and won't play anything. I'm tring to record from internet radio. What's the secret to make Audacity work in Ubuntu 8.10? Thanks for any help.

---

### Post by Spaceman9 on 2008-11-02
bump.

---

### Post by Spaceman9 on 2008-11-03
UPDATE!!!
I looked at  a lot of threads about pulseaudio including this one [http://www.pulseaudio.org/wiki/PerfectSetup#Audacity](http://www.pulseaudio.org/wiki/PerfectSetup#Audacity)

It says:
> "Audacity

Audacity doesn't support PulseAudio, nor Esound for the moment. You'll have to kill or suspend pulseaudio before you use this application. Audacity uses the PortAudio cross-platform Audio API which doesnt support pulseaudio. Some work was started on making portaudio support PulseAudio but this does not appear to be under active development currently and does not work in it's current state.

Audacity can use OSS for sound input and sound output. By changing the 2 settings in preferences to /dev/dsp, and running audacity as

padsp audacity

you route OSS sound through pulseaudio and can have successful playback and recording with audacity. You could also set the sound input to be ALSA which (for regular users) is less likely to be blocked by another application, as recording with multiple applications at once is less commonly done

Using pasuspender to momentarily suspend pulseaudio is another way to use Audacity.

pasuspender -- audacity <argument>

You could also run the windows version through wine, to have proper pulseaudio support"  


So, Audacity doesn't support PulseAudio! I can't uninstall pulseaudio because when I tried to do that it wanted to uninstall gnome-desktop because pulseaudio is installed now with the gnome-desktop. 

Does anybody know if Kubuntu has pulseaudio? I already had KDE3.x installed in Ubuntu and when I upgraded to Ubuntu 8.10 online it uninstalled KDE3.x and installed KDE4.x.

The buntus are gong from bad to worse for anyone who has to use Audacity. The only thing I can record in now is Linux Mint.

---

### Post by Spaceman9 on 2008-11-05
I found a solution for the problem with recording and editing sound in Ubuntu 8.10 with Audacity. It's called  Kwave! It's a KDE app. Kwave doesn't have any problems with Pulseaudio. I don't think it uses Pulseaudio.

Kwave is in the Ubuntu repos. If you want to build it from code for KDE4 it's here [http://www.kde-apps.org/content/show.php?content=11781&forumpage=1&PHPSESSID=e5af](http://www.kde-apps.org/content/show.php?content=11781&forumpage=1&PHPSESSID=e5af)

The only problem with Kwave is it can't save Mp3. Now I need to find a converter from ogg to Mp3. The journey continues.

---

### Post by FinnCoder on 2008-11-05
I have this same problem with Audacity and Ubuntu Intrepid. Annoying! I have to try that kwave also.

Edit: there's a Pulseaudio compatibility plugin for ALSA (package libasound2-plugins?). It should enable sounds for ALSA applications (like Audacity) that don't support Pulseaudio explicitly.

Edit: Also look at this: [http://forums.debian.net/viewtopic.php?t=12497](http://forums.debian.net/viewtopic.php?t=12497)

---

### Post by Spaceman9 on 2008-11-05
Thankx for the link FinnCoder. No joy though. I'm gong to look at Linux Mint Gnome. Audacity just works in Linux Mint KDE. I don't understand what Mark Shuttleworth is thinking.

---

### Post by Spaceman9 on 2008-11-06
FinnCoder I found out Ubuntu doesn't have everything for Pulseaudio installed. I added:

libpulse-mainloop-glib0
padevchooser
pman
paprefs
pavucontrol
pavumeter
pulseaudio-module-zeroconf

If you add those packages from the repos Audacity will work except for one thing. After you record anything save it before you edit it.

---

### Post by Ascenti0n on 2008-11-06
Hi Spaceman9

I'm having the problems recording too, but it isn't an audacity issue.

In System>preferences>sound you can choose options for the capture settings, on my system there are many. I tried various settings with ubuntus' basic recording software: applications>sound and video>sound recorder, and nothing works, the sound recorder app even freezes on 'pulse audio' I think.

I'm currently searching to find solutions, but there isn't anything obvious other than posts complaining about 'pulse audio server', perhaps our problems lie here?

---

### Post by Onesimus on 2008-11-06
I am using Hardy Heron, so my solution may not solve your problem (?) - but still perhaps worth a try.  I downloaded the latest version of Audacity (1.3.6) and experienced similar problems with no sound.

Here is what I did to make sound work.
In Audacity, go to Edit->Preferences->Audio IO and change the playback device setting from digital to analog.  Mine currently is set to:
ALSA: HDA Intel: STAC92xx Analog (hw:0,0)

it was

ALSA: HDA Intel: STAC92xx Digital (hw:0,1)


Hope this helps

---

### Post by Spaceman9 on 2008-11-07
Ascenti0n in the Sounds I have:

Sound Events
Sound playback: Autodetect

Music and Movies
Sound playback: Autodetect

Audio Conferencing
Sound playback: Autodetect
Sound capture: C-Media Cml8738 (model 37) C-Media PCI DAC/ADC (ALSA)

Default Mixer Tracks
Device: C-Media Cml8738 (Alsa mixer)


In Audio I/O in Audacity I have:

Playback
Device: ALSA: C-Media Cml8738: C-Media PCI DAC
Using: Portaudio v19

Recording
Device: OSS: /dev/dsp
Channels: 2 (stereo)

I think you're right about the problem being pulseaudio. Last year Mandriva tried pulseaudio and they told people it didn't work for to uninstall it.



Onesimus Thanks for your help. I don't have a digital sound card. Just an old analog sound card. It's good to know pulseaudio doesn't seem to work with digital sound cards either. I think Ubuntu is trying to use too many new things too soon. Kubuntu and Linux Mint 5 KDE don't have pulseaudio so Audacity doesn't have any problems with them.

---

### Post by FinnCoder on 2008-11-10
I haven't tried to record anything lately, but I noticed that running "pasuspender audacity" and changing the output plugin to OSS works just fine for me. At least Audacity can output sounds perfectly that way under Intrepid. Soundtracker also works fine with pasuspender :)

---

### Post by SR_ELPIRATA on 2008-12-30
Well, I can say I had this same problem. That Ambient radio station that is included with Rythmbox is superb, but as some said, it would be nice to have some of that stored.

I honestly find that pulseaudio on 8.10 works a LOT better than in 8.04. Pulseaudio project page says that for 8.04 the implementation was poorly done (not their fault) but in 8.10 that would be fixed.

Of all the suggestions listed on this thread, using wine is the simpler one. I'm using audacity thru wine 1.1.11 and its working great. Once app was intalled I made sure it was recording in 2ch mode (I plan to test the 6ch someday) and then started monitoring the source.

Level bars were moving well and I did a test recording with it and it worked fine. So I dont really understand all the fuzz about going to another linux version and all. It does work.

Now that it does work, I assume that EZCD extractor software trial should work as well via wine, therefore, converting formats should be piece of cake. Solutions in this case might not be native, but they do work.

PS: Wanted to add, btw, that previously, my 5.1 soundcard would never work under 7.10 but even in the poorly implemented 8.04... making it work it was a matter of editing a text file, changing a 2 for a 6 and pop some multichannel audio/video file to test and it worked. So, pulseaudio is great to me.

---

