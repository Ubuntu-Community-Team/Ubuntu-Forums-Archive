---
title: "SMPlayer failing to pass file to mplayer"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by Robbyx on 2008-04-06
Videos are playing in mplayer.

The same videos when opened in SMPlayer produce an immediate error message:

> MPlayer has finished unexpectedly: Exit code 1.

> /usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -zoom -nokeepaspect -framedrop -autosync 100 -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 54525966 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast -1 -brightness -6 -hue -6 -saturation 1 -volume 40 -nocache -osdlevel 0 -idx -vf-add pp -autoq 6 -vf-add screenshot -vf-add eq2,hue -channels 2 -af volnorm=2 -softvol -softvol-max 110 /media/flm/English.rmvb

I get the same error message whatever the type of file eg avi

I am using v .6.0rc3 with qt4.2.3 in Ubuntu Gutsy

I would appreciate some help because I used SMPlayer in Fiesty and would like to continue to use now I am in Gutsy.

---

### Post by Robbyx on 2008-04-06
I was not able to find this problem answered elsewhere. Could I please have a reply.

Robin

---

### Post by rvm4000 on 2008-04-06
You don't say the error from mplayer, but I guess it's because of the -volume option. 

Disable the option "Change volume just before playing" in Preferences->General->Audio.

That option requires a patched mplayer to work.

---

### Post by Robbyx on 2008-04-07
Thank you. You picked up the cause and now it works well.

I notice in the preferences there are options for mplayer. In order to have the best quality playback are there any optimising settings I should include in the options?

Robin

---

