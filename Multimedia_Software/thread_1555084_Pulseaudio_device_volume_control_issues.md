---
title: "Pulseaudio device volume control issues"
date: 2010-08-17
forum: Multimedia Software
---

### Post by superppl on 2010-08-17
Hello,

I'm having a problem with pulseaudio. Audio works almost perfectly, but the volume control is off. Specifically, adjusting the volume for the output device is problematic.
[[IMG]http://img444.imageshack.us/img444/8166/snapshot3m.png[/IMG]](http://img444.imageshack.us/i/snapshot3m.png/)
I'm talking about this right here. About 20% to 100% is the same, producing maxed volume.

I'm not sure if this is relevant, but I've been watching how the volume control influences volume levels in alsamixer. I use F6 to choose my actual sound card, so I can see all of the channels. That entire 20% to 100% is controlling a channel called "Master Front" (or I think it's called that... It gets cut off right at the F), and then the final few volume levels modify "Front" and "PCM".
I suppose a solution would be make the volume control within pulseaudio influence another channel, but I have no idea how to do that.

I'm running Kubuntu 10.04, and my sound card is a HDA ATI SB.

---

### Post by superppl on 2010-08-17
I found something helpful.
This post specifies how to do what I want, but I'm still having issues. [http://ubuntuforums.org/showthread.php?t=1529806](http://ubuntuforums.org/showthread.php?t=1529806)

Specifically, > 
You may find that the above workaround is insufficient, in which case you may configure PulseAudio to control only one mixer control, e.g., PCM (cf. alsamixer). Find the row saying "#load-module module-alsa-sink" and change it to:

load-module module-alsa-sink control=PCM

(remember to remove the # in the beginning of the row!) Optionally replace PCM with the mixer control you want PulseAudio to control.

You will then need to killall pulseaudio as above and allow the daemon to autospawn. 
causes
```
E: module.c: Failed to load  module "module-alsa-sink" (argument: "control=PCM"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
```

If I comment out this line, pulseaudio starts fine, but then the volume control doesn't appear to do anything.

I thought I might also add that if I leave that line as ```
load-module module-alsa-sink
``` then I still get ```
E: module.c: Failed to load  module "module-alsa-sink" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
```

---

### Post by superppl on 2010-08-17
This line ```
load-module module-udev-detect ignore_dB=1
``` appears to have solved my problem.
A little stupid, but this *always* happens with me. I scourge every piece of documentation I can find, still can't solve the problem, and give up and ask for help. Then I find the solution on my own. :/

---

