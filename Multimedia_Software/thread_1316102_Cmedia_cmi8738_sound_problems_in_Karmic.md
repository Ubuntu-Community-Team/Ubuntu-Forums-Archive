---
title: "Cmedia cmi8738 sound problems in Karmic"
date: 2009-11-05
forum: Multimedia Software
---

### Post by feroxy on 2009-11-05
Seems like I'm probably going to be a drop in an ocean of sound problems here, but here goes...

Just to preface this, my sound was working perfectly fine before this upgrade. 
After the upgrade, when I play anything (audio or video) it will play for a short while then stop and the sound will just turn to clicks and pops (not stuttering really as others report). When this happens I notice that the "pulseaudio" process starts eating all cpu time, even for a short while after I close the app I was using for playback.

The problem seems worse when using Totem for playback (or perhaps more specifically Gstreamer since Miro has the same problem and it uses gstreamer too) rather than my usual SMPlayer (mplayer backend). The same problem is there in both but it typically takes longer for it to trigger in smplayer and I can usually recover in smplayer by pausing for a few seconds and doing a seek back or forwards which is not usually possible in totem or miro. Symptoms when playing video are that the video freezes (probably due to the aforementioned pulseaudio cpu hogging) although in smplayer sometimes picture will continue while sound devolves into the clicks and pops. In totem I notice that the play counter (elapsed time) will start racing forward very quickly a few seconds after sound stops.

Would really love a fix for this, it is seriously hampering my use of this computer. Any help appreciated. 

audio hardware is:
 0 [CMI8738        ]: CMI8738 - C-Media CMI8738
                      C-Media CMI8738 (model 37) at 0xa400, irq 10

I also saw something somewhere about creating a pulseaudio log, which I did and noticed these errors popping up in it while trying to play an mp3 podcast:
```

E: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 4294953200 bytes (24347807 ms).
E: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_cmipci'. Please report this issue to the ALSA developers.
```and
```
E: alsa-util.c: snd_pcm_delay() returned a value that is exceptionally large: 393012 bytes (2227 ms).
E: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_cmipci'. Please report this issue to the ALSA developers.
```full log is at [http://pastebin.com/m2dc29a91](http://pastebin.com/m2dc29a91)

---

### Post by ziphi on 2009-11-06
I have encountered the same problem and not been able to solve it yet.
Any help appreciated!

edit: I temporarily solved the problem using this method:

```
sudo apt-get --purge remove pulseaudio && sudo apt-get install esound
```
then reboot. Sound works fine now, no stops, no stuttering, no skipping or fast forwarding. AlsaMixer works as well.
Conclusion: On my system, PulseAudio doesn't work out of the box and none of the countless fixes helped, so I'm dropping it.

Greetings,
ziphi

---

### Post by feroxy on 2009-11-06
Thanks, good to know there may be a possible way to avoid the problem.

However, in the hope of maybe getting the problem found and fixed I have submitted a bug report at [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/476652](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/476652) You could chime in with your own experiences if you like.

If there's no movement I'll be giving your solution a try.

---

### Post by ziphi on 2009-11-06
I'm not an expert, but I've been looking for a fix to get pulseaudio working for quite some time without success. I know pulseaudio is the system that comes with and is the out-of-the-box magic solution of Karmic Koala. This is the choice of the developers and it will probably be updated for the next few releases. However, since it doesn't work for me, I step back to a second choice solution. I won't be looking for a solution for the pulseaudio problem any further, since esound does everything I need. No messing around with my sound anymore.

Bye,

ziphi

---

### Post by siliconmeadow on 2009-11-08
I'm not familiar with your hardware, but I found this thread:

[http://ubuntuforums.org/showthread.php?t=1309666](http://ubuntuforums.org/showthread.php?t=1309666)

and in particular, michaelzap's comment, fixed my problem:

> If there is a proprietary driver for your internal modem (which in my case is a sub-element of my Intel sound card) listed in System -> Hardware Drivers try removing it. I did this and suddenly I had sound and the device is visible in the Sound Control Panel. I still have other problems, but at least I have sound.

---

### Post by feroxy on 2009-11-08
No onboard modem unfortunately so no driver listed :(

thanks though :)

---

### Post by fenixk19 on 2009-12-25
I'm experiencing the same problem. Please tell, if it is already fixed in some way.

---

### Post by feroxy on 2009-12-26
Unfortunately no, and no response to my bug report either.
Here is what I have do to get a (sorta) working sound system, rather than remove pulseaudio completely:

-make a file in /home/<username>/.pulse/ called client.conf, add the line "autospawn = no" to it (without the quotes) and save. (show hidden files in nautilus to get to this folder). This allows pulseaudio to be killed and not start up again.
-now open a terminal and type "pulseaudio -k" (you should see the volume icon disappear)
-Since klling pulseaudio means that there is no volume control applet, you will want to install gnome-alsamixer from apt-get or synaptic package manager. This will show up in Applications/Sound&Video
-check if sound plays using something other than the built in movie player (vlc or smplayer), but be warned as volume may be up to 100% 

In order to kill pulseaudio on every login, I also did the following:

-from gnome menu, System/Preferences/Startup Applications
-Click add and enter the command "pulseaudio -k" (again no quotes when you enter it) You can also write a name and comment. I used "PULSEAUDIO DIE DIE DIE" as the name and a comment along the same lines. You may choose to be more mature about it.
-click save and close out.

Caveats:

*The movie player app (totem) will no longer play sound after this, nor can I get banshee to play audio. I think those use gstreamer on the backend so other apps that use gstreamer may fail too. In theory I think one should be able to select alsa using the command "gstreamer-properties". In my case the test works when I select plugin ALSA and device "cmedia pci DAC/ADC" but the apps themselves still wont work. If anyone else can figure this out, do post here.
In practice this doesn't really affect me much since I use SMPlayer or VLC to play my audio and video plus other apps may work too if you can check their preferences and set them to use alsa directly.
*I have also noticed that sound will sometimes stop for some reason and no app can play. To fix this, I use the command "sudo alsa force-reload" and all works again.
*The other problem I found was that occasionally and especially during longer play sessions, the sound will appear to "crash". It becomes a *very* loud repeating loop of sound. So keep the physical volume control of your speakers/headphones close by and close the app when this happens. It should eventually stop and you can resume play.

Hopefully this helps somewhat. Would still prefer a proper fix to pulseaudio though, but I don't know how to get a proper response from anyone "official"

---

### Post by fenixk19 on 2009-12-27
Well, i've removed pulseaudio, but other problem disturbs me. It is random sound glitches during playing sounds with alsa. I think, it is the same problem, that kicks out pulseaudio:
```

E: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 4294953200 bytes (24347807 ms).

```
I mean, that during playing snd_pcm_avail returns bad value, and player restarts playing, but not as pulseaudio. It starts playing from the same place, where it stops, so there is a little glitch. The question is: how to prevent snd_pcm_avail from returning wrong value?

---

### Post by feroxy on 2009-12-27
Could you do me the favour of posting your experiences in the bug report I opened? Maybe if it gets more activity it will get some attention:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/476652](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/476652)

Something has clearly gone wrong where this sound device is concerned in 9.10. It worked 100% fine in 9.04 :(

---

### Post by kimdino on 2010-01-04
Adding my voice to feroxys. 
This problem seems to affect a lot of people but it appears to be a low priority on the devs list. Could this be because few are bothering to report it through the official channels?

Please add to feroxys bug report.

---

### Post by jbwiv on 2010-02-11
I've had the same problem, but reported it here at the alsa project instead, as that's what the error message said to do: 

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4911](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4911)

I'll add my name to your ticket as well.

Thanks,
jbwiv

---

