---
title: "[SOLVED] SMPlayer"
date: 2008-07-29
forum: Multimedia Software
---

### Post by Robbyx on 2008-07-29
I find that when I play video files there is no sound to start with. I have to choose an extra video filter and then sound switches on. Why is this?

---

### Post by rvm4000 on 2008-07-29
Have you tried to select another audio driver in Preferences -> General?

---

### Post by Robbyx on 2008-07-30
I have tried switching drivers and thought that was the solution because I found it to work without having to choose an additional video filter. I then found that watching other videos required me to still choose a new filter. I guessed this was because the videos were remembering their old settings. I unticked that box but it did not bring back the sound when starting the video, without choosing a video filter. I have also noticed that the when I go fast forward the sound is lost and will not return unless I restart the video. I am wondering if smplayer has become corrupted and suggest I  reinstall both smplayer and mplayer. Do you concur or is there something else that needs reinstalling as well; I am thinking of codecs?

Whilst you are dealing with me  could you please suggest some set up strings so that the deblock and denoise normal are automatically applied to all videos? I am refering to the smplayer prefs--advanced--options for mplayer.

---

### Post by rvm4000 on 2008-07-30
> **Robbyx said:**
> I have tried switching drivers and thought that was the solution because I found it to work without having to choose an additional video filter. I then found that watching other videos required me to still choose a new filter. I guessed this was because the videos were remembering their old settings. I unticked that box but it did not bring back the sound when starting the video, without choosing a video filter. I have also noticed that the when I go fast forward the sound is lost and will not return unless I restart the video. I am wondering if smplayer has become corrupted and suggest I  reinstall both smplayer and mplayer. Do you concur or is there something else that needs reinstalling as well; I am thinking of codecs?

This is a really strange problem. It seems the sound is lost somehow during playback and the only way to restore it is by restarting mplayer. 

I'd suggest: 

 - delete the smplayer config files (*~/.smplayer/smplayer.ini* and *~/.smplayer/smplayer_files.ini*) to start with a clean configuration.

 - install the latest version from svn: [ftp://ftp.berlios.de/pub/smplayer/ubuntu/](ftp://ftp.berlios.de/pub/smplayer/ubuntu/)

If that doesn't fix the problem, try to enable the option "Use software volume control" in Preferences -> General -> Audio. Also take a look at your sound mixer and be sure the volume is not too low.

If you still have problems, take a look at the mplayer log (Options -> View logs) when the sound is lost, maybe there's a warning or error message there.

> **Robbyx said:**
> 
Whilst you are dealing with me  could you please suggest some set up strings so that the deblock and denoise normal are automatically applied to all videos? I am refering to the smplayer prefs--advanced--options for mplayer.

Add **pp=vb/hb,hqdn3d** to the "video filters" field.

---

### Post by Robbyx on 2008-07-31
I followed your advice and it has made a difference. Thank you. The sound is there. I have just tried it on an avi file and this is the log result under the exit code: 1. Can you see something I need to do?

> /usr/bin/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -zoom -nokeepaspect -framedrop -autosync 100 -stop-xscreensaver -*** -embeddedfonts -***-color ffff0000 -***-border-color 00000000 -subfont-autoscale 1 -***-font-scale 1 -subcp ISO-8859-1 -subpos 100 -volume 65 -cache 3000 -osdlevel 0 -idx -vf-add yadif=1 -vf-add pp -autoq 6 -vf-add pp=vb/hb,hqdn3d -vf-add screenshot -vf-add eq2,hue -channels 2 -af volnorm=2,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/flm/The.avi

When I run the file direct under mplayer it does play. It is not running under smplayer.

---

### Post by rvm4000 on 2008-08-01
There's no error message in the log, but I see something: **-volume 65**. 
Set the option "Change volume just before playing" in Preferences -> General -> Audio to No.

(The *-volume* option is not available in the official mplayer, a patch is required)

---

### Post by Robbyx on 2008-08-01
That adjustment has made a difference. The avi files now play from smplayer. Thank you for your help.

---

