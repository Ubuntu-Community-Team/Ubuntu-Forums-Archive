---
title: "Hardy sound problem."
date: 2009-04-28
forum: Multimedia Software
---

### Post by Snyper64 on 2009-04-28
I am trying to get my surround sound working but am having some problems. I am using a Turtle Beach Audio Advantage USB sound card which worked fine in Gutsy and previous releases for passing Dolby Digital and DTS sound to my reciever(Logitech z-5500) but since I installed hardy and am forced to use Pulse Audio I can no longer get my computer to pass DD & DTS streams to my reciever, only stereo. I have followed several guides and thought I had it working at first(Totem Xine played my DVDs in DTS & DD but it was only because Pulse Audio was disabled as you will read below) but none of my other media players would work no matter what I did. I had somehow stopped Pulse from starting as my sound server when I configured the file "default.pa" and added in "load-module module-alsa-sink device hw:1,0"(yes in the correct place and correct device). I removed that line and restarted and everything is back to normal. I also tried modifying "daemon.conf" and modified the following line to "default-sample-channels = 6"(originally set to 2 for stereo sound) but to no avail.

I tried to test my surround sound but got this error:```
snyper64@snyper64-desktop:~$ speaker-test -Dplug:surround51 -c6 -l1 -twav
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
``` It looks like ALSA is trying to use the wrong hardware(I have no other sound card anymore and this one should be set to 1 not 0). Any ideas on how to fix this and get pulse to pass the DD & DTS to my reciever?

Any help would be very appreciated.

---

### Post by markbuntu on 2009-04-28
Did you try this?

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

Once you figure out the device you can make one in asoundrc and then load it in default.pa. There are some old threads around here about making a A52 passthrough device but I do not have that info.

---

### Post by Snyper64 on 2009-04-28
Well I installed Audacious and downloaded some test files and got that to put out DTS sound but as soon as i tried playing the same files through Pulse it just played them in stereo(EDIT: If I check bypass all signal processing if possible it plays in DD or DTS but I think its because Audacious skips using Pulse). Pulse is using the right device but it is processing the sound and outputting it as stereo. Any idea on how to stop Pulse from doing this?

---

### Post by Snyper64 on 2009-04-29
Ok, I was messing around with VLC and got that to work with AC3, now if i could just get Totem-Xine to use Alsa and allow AC3 pass through I would be set as I hardly ever use M-Player to play AC3 files. Is there any kind of configuration file(s) I can edit manually to get Totem to do what I want?

---

### Post by Snyper64 on 2009-04-29
Ok, I finally got Totem-Xine to pass AC3 sound, If you are having problems with getting surround sound to work you have to manually modify xine_config.```
gksudo gedit ~/.config/totem/xine_config
```
Look for this line:```
# device used for pulseaudio
# string, default: 
# audio.pulseaudio_device:
```
and chang it to this:```
# device used for pulseaudio
# string, default: 
audio.pulseaudio_device:hw=1.0
```
change hw=1.(yes its a dot not a hyphen)0 to whichever your digital out card and device is.

I also changed the above line to this:```
# audio driver to use
# string, default: auto
audio.driver:Alsa
``` but it might not be necessary for you. Also make sure that you have AC3 Pass through selected in audio preferences in Totem.

Now to get M-Player to work for those few files that have surround sound though this would have been a lot easier if the Ubuntu team would have integrated Pulse right.

---

