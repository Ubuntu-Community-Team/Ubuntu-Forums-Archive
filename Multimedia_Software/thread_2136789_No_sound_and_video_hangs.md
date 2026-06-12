---
title: "No sound and video hangs"
date: 2013-04-18
forum: Multimedia Software
---

### Post by StuckedOnWeb on 2013-04-18
[COLOR=#333333][FONT=Ubuntu Beta]I am struggling with no sound problem on Ubuntu 12.04 and now on 12.10. I went through a lot of forums mentioning this issue and I have tried a lot of different solutions that worked for others but not for me. There is no sound from speakers when trying to play video from Youtube and the video from local disk does not start at all unless I do[/FONT][/COLOR]

sudo aptitude reinstall alsa-utils
[COLOR=#333333][FONT=Ubuntu Beta]
After the reboot everything works fine but after another reboot there is no sound again. So if I want to have the audio output on the next boot I have to reinstall alsa-utils before shutting down the system :)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I have tried to install alsa-utils not from repository but from the developers site but it did not help, do you have an idea where could be the problem and why the sound works only for the first time the system is on?

If it helps I am using vga_switcheroo to switch turn off discrete graphics on start.

When there is no video or sound and I type aplay -l into the terminal it just hangs and there is no output. After the package reinstall and reboot the output from aplay looks like this:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]** Seznam PLAYBACK Hardwarových za&#345;ízení ****[/FONT][/COLOR]

[LIST]
[*]karta 0: Intel [HDA Intel], za&#345;ízení 0: ALC271X Analog [ALC271X Analog] Podza&#345;ízení: 1/1 Podza&#345;ízení #0: subdevice #0
[*]karta 0: Intel [HDA Intel], za&#345;ízení 1: ALC271X Digital [ALC271X Digital] Podza&#345;ízení: 1/1 Podza&#345;ízení #0: subdevice #0
[/LIST]

---

