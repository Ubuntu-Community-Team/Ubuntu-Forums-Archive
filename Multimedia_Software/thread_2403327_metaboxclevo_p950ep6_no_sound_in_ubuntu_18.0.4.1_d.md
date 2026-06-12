---
title: "metabox\clevo p950ep6 no sound in ubuntu 18.0.4.1 desktop lts"
date: 2018-10-10
forum: Multimedia Software
---

### Post by svyr on 2018-10-10
hello,

followed guide here [https://gist.github.com/Brainiarc7/f7da590bee1ed35ac5ed258ff9335fd6#file-installing-linux-on-eurocom-q6-md](https://gist.github.com/Brainiarc7/f7da590bee1ed35ac5ed258ff9335fd6#file-installing-linux-on-eurocom-q6-md) for my new P950ep6 – got almost everything working ok .


The trouble is audio – tested it with win10 – works ok [dual boot just for this]

in ults 18.0.4.1 live or installed – i get no output to speakers or to headphones [haven't really tried the hdmi audio but nvhda is up for the installed edition] – either via touching the volume slider, or chrome or aplay etc.

seems to have intel pch audio/realtek alc1220

The extent of messing with audio was the pulse config in the above link for spdif
not working before though.

I'm not hugely familiar with what I should see in alsamixer or pavucontrol
but I suppose- I've tried the different profiles (incl ones for analog output and none of the volumes look muted, auto mute is off. You can see the level audio peaks when sound is output in pavucontrol but no actual sound

does anyone have any suggestions/managed to get it to work?

---

### Post by svyr on 2018-10-10
Some of usual command output is here [http://forum.notebookreview.com/threads/metabox-p950ep6-no-sound-in-ubuntu-lts-desktop-18-0-4-1.824939/](http://forum.notebookreview.com/threads/metabox-p950ep6-no-sound-in-ubuntu-lts-desktop-18-0-4-1.824939/)

my alsa info output is here [http://www.alsa-project.org/db/?f=23dc54d8214dff59af255aac661a31e2be286af5](http://www.alsa-project.org/db/?f=23dc54d8214dff59af255aac661a31e2be286af5)

---

### Post by svyr on 2018-10-18
here's the pulseaudio -vvvv outputs with a couple of apps - still not working please help. 
[https://paste.ubuntu.com/p/7DBmfBVqkH/](https://paste.ubuntu.com/p/7DBmfBVqkH/)

---

### Post by svyr on 2018-10-19
[INDENT] 					 					hmmm it looks like maybe it's already fixed in the new alsa builds. 
basically nothing worked and I nearly gave up but found this guide
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) 

step 4 and just adding the ppa and installing the hda audio daily build works

sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily

sudo apt-get update

sudo apt-get install oem-audio-hda-daily-dkms

reboot

then both alsa and pulse audio outputs work 					 
 				[/INDENT]

---

