---
title: "Beats audio not working"
date: 2013-12-27
forum: Multimedia Software
---

### Post by ak13_6 on 2013-12-27
Hello,
I have hp envy 15z-j100 laptop powerd with beats audio. after installing ubuntu 13.10 beats audio are not working, i.e subwoofer and two speakers are not working. I tried to fix this issue by following this


[LIST=1]
[*]Firstly you will need to install hda-jack-retask tool; which mainly helps us to re-task the audio jack pins on our motherboard.
[*]sudo apt-add-repository ppa:diwic/hda
[*]sudo apt-get update
[*]sudo apt-get install hda-jack-retask
[*]hda-jack-retask &
[*]Open hda-jack-retask
[*]Select the IDT 92HD91BXX codec (may be different on other models;  but definately other than your on-board controller i.e., Intel-XXX).
[*]Check the “Show unconnected pins” box (the internal speakers do not show as connected)
[*]Remap 0x0d (Internal Speaker, which is your Front side) to “Internal speaker”
[*]Remap 0x0f (“Not connected”, which is the under-display speakers) to “Internal speaker”
[*]Remap 0×10 (“Not connected”, which is the subwoofer) to “Internal speaker (LFE)”
[*]Apply & test audio output with any media player.
[*]Select “Install boot override” to save the settings to apply at boot time.
[*]Reboot. When it comes back, you should have full sound from all  speakers. Also test headphones. Plugging in headphones should disable  sound from all internal speakers.
[/LIST]

But i am not able to procced after step 4, because it show an error. following is the error snippet
$ sudo apt-get install hda-jack-retask
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package hda-jack-retask


I dont have this package, i  tried to search on internet but i didn't get.
please help me with this

Thank you

---

### Post by Yellow Pasque on 2013-12-27
> Note: as of Ubuntu 13.10, hda-jack-retask is part of alsa-tools. Just install the alsa-tools-gui package from the regular archive and start "hdajackretask". (Note: if you don't have a .pulse directory, try symlinking .pulse to .config/pulse - and remove the symlink again when you have closed hda-jack-retask.)

-- [https://launchpad.net/~diwic/+archive/hda](https://launchpad.net/~diwic/+archive/hda)

---

### Post by ak13_6 on 2013-12-30
Thank you for the help appreciate that,
I dont have pulse directory, and i am very naive to ubuntu. can u please guide me step by step how to "symlinking .pulse to .config/pulse - and remove the symlink again when you have closed hda-jack-retask".
I am not getting this part.
Thank you.

---

### Post by Yellow Pasque on 2013-12-30
I'm not even sure if it's still necessary, but you would:
```
cd ~/
ln -s .config/pulse/ .pulse
```

---

### Post by ak13_6 on 2013-12-31
i executed this code on terminal, but after that my system is not sounding. no sound at all.

---

### Post by Yellow Pasque on 2014-01-02
Then delete the symlink you created and reload pulseaudio:
```
 rm -r ~./config/pulse*
rm -r .pulse
pulseaudio -k
```

---

