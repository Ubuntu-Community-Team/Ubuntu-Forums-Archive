---
title: "Problem with volume control pulse audio not starting"
date: 2010-07-11
forum: Multimedia Software
---

### Post by ypestis on 2010-07-11
Dear forum,

I can't go to my sound settings anymore nor control my volume with the volume buttons on my laptop nor can I open the volume settings...

I get an error saying "waiting for sound system to respond"

I've tried reinstalling pulseaudio but without any luck..

The sound is working good but I can't use my volume control anymore..

Anything I can do?

Thanks alot!

---

### Post by WinterRain on 2010-07-12
I would *completely remove* pulse audio *and* alsa and rebuild alsa with module assistant. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
then
```
sudo apt-get install module-assistant
```
then
```
sudo m-a a-i alsa
```
then
```
sudo apt-get install alsamixer
```

I've tried it before and worked for me. It's up to you whether you reinstall pulse.

---

### Post by ypestis on 2010-07-12
Hi thank you for your help.

I know there is a command for emoving pulseaudio
```
sudo apt-get autoremove pulseaudio
```

Do you know if there a same thing for ALSA?

Also I've noticed one pulseaudio is gone I can't control ALSA from the panel and with my buttons, is there anyway to do this?

cheers

---

### Post by ypestis on 2010-07-12
Oke that didn't fix it...

When I go to the command prompt and do
pulseaudio

I get the following:

E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

If I go to sound options I get
waiting for sound system to respond

The last thing I did was enabling a plugin from Exaile called:
MPRIS
Description:Creates an MPRIS D-Bus object to control Exaile

I wanted to contrl Exaile from Ciaro Dock.. after that I noticed my volume control button's where not working anymore.... I dont know if this has to do with the situation...

---

### Post by ypestis on 2010-07-12
I went back to my backed up setting like just after I got the bug and just tried to reinstall pulseaudio.
autoremoving it and installing it again from the command prompt.

Now the volume speaker in the panel is gone. if I do pulse audio in the command prompt I get:

E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
E: module-ladspa-sink.c: Master sink not found
E: module.c: Failed to load  module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master= plugin=mbeq_1197 label=mbeq control=-30.0,-9.0,-4.8,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialise daemon.

By the way all sound is working on my system :/

---

### Post by itsdaveperdue on 2010-07-13
> **ypestis said:**
> I went back to my backed up setting like just after I got the bug and just tried to reinstall pulseaudio.
autoremoving it and installing it again from the command prompt.

Now the volume speaker in the panel is gone. if I do pulse audio in the command prompt I get:

E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
E: module-ladspa-sink.c: Master sink not found
E: module.c: Failed to load  module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master= plugin=mbeq_1197 label=mbeq control=-30.0,-9.0,-4.8,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialise daemon.

By the way all sound is working on my system :/

Try this:
1) Remove the indicator applet from the panel (little mail envelope with missing volume icon).

2) sudo apt-get install --reinstall indicator-applet

3) sudo apt-get install --reinstall indicator-sound

4) add the indicator applet back to panel.


Worked for me.

---

### Post by ypestis on 2010-07-13
That did bring back my speaker icon on the panel but it's still not responding on the volume up/down and mute buttons.. also if I want to go to sound preferences I get the " waiting for sound system to respond"

---

### Post by lidex on 2010-07-14
Your pulse config may be a problem, you can safely remove these files.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by sailingboarder on 2010-07-14
I am having the same problem. I tried all of these solutions, but it did not seem to fix it.

---

