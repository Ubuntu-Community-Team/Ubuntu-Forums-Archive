---
title: "microphone &amp; sound recorder problem"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by toastedcheese on 2007-02-12
I hate to post about this, since there are so many other threads out there regarding mike problems, but I'm pretty stuck.

My brand new mike is not recording. There's feedback from the speakers when I make noise, but whenever I attempt to record using Sound Recorder, it doesn't seem to start recording and the resulting file has no data. At this point, when I press the record button again or try to close the program, it crashes. The device I SELECT under "Record from input" doesn't seem to make a difference.

I've fiddled with the settings in alsamixer, alsamixergui, and the volume control on the desktop - most recently I attempted to follow the advice [here]("http://ubuntuforums.org/showthread.php?p=2139193#post2139193") - but it hasn't fixed the problem.

A couple days ago, I tried using OSS instead of ALSA. The result was that the Sound Recorder did not crash and actually tried to record something - instead of "Ready," it showed the seconds ticking by - but there was still no audible sound. Unfortunately, I can't replicate that now; when I change to OSS through my volume control or my "Sound" settings under preferences, Sound Recorder still gives me the ALSA devices to choose from. I think there might be a third menu controlling sound that I got to through the console, but I've forgotten the command.

I also tried Audacity and Praat; they haven't crashed but neither do they record any sound. And just now, after some more fiddling with the alsamixer and ALSA/OSS settings, they've both stopped working. Audacity is complaining of an "error while opening sound device. please check the input device settings and the project sample rate." I've tried to undo whatever I did, but I can't figure out what that was.

So: suggestions? Things you need me to post?

---

### Post by tedrogers on 2007-02-14
I can't get mine to work in Skype / Ekiga, and have been trying for ages, but I have managed to get it recording into Audacity and monitoring the incoming level - proving that the hardware works.

Feedback - get rid of this by muting the microphone playback, leave the capture enabled. Just like in Windows you have playback and record mixers, just mute the mic on the playback side of things.

Run alsa-mixer from a terminal (if you haven't got it then search for alsa-utils in the repo's / synaptic). Navaigate around it and ensure that CAPTURE in red is highlighted under MIC, ADC & CAPTURE. Also enable to Mic Boost if you want. TAB key moves around and up/down arrows change levels, SPACE sets caputure where you want it, ESC to exit.

If you do this you should be able to run Audacity (also in repo's) and assuming you set the sound device to use OSS, then you should be able to monitor the mic signal and record your own voice.

I would be interested to hear if you are also able to use the SKYPE TEST CALL (Skype available from Skype website, choose the Debian package for Ubuntu) - this is the only thing I can't get to work and it's taken me months and months of trying. I heard something today about making sure that full duplex recording is enabled, and maybe this will fix it when I test later on (if I can find the relevant option).

Hope this helps.

---

### Post by tedrogers on 2007-02-14
Just as another update, using OSS I have been able to get Gizmo phone working...yay!

Shame all my credit is on Skype...but its a start.

Skype must be a bag of crap on Linux IMHO.

---

### Post by toastedcheese on 2007-02-15
I turned the capture on for ADC and tried switching to OSS, but Audacity is still putting up the same error message as before, so that I can't record anything. And Sound Recorder is still crashing. The Audacity crashing is fairly new; I can't figure out for the life of me what I did to cause it.

Incidentally, whereas many of the items under Capture in alsamixer have volume bars above them, Mic and Mic1 don't (although they do have "capture" in red above them.) I can't change this. Could this be indicative of a problem?

Thank you for the suggestions!

---

### Post by tedrogers on 2007-02-16
No, the different OSS volume controls are just the way they are...this is normal.

I don't know what else to suggest - it seems very unstable on the whole and some people get it to work while others don't. After all it took me 6 months to get it working and I don't really know what I did or how to make it repeatable. Sorry.

---

### Post by drpaul on 2007-02-16
Have you tried upgrading the version of the Alsa driver? It helped me a lot.

Paul

---

### Post by tedrogers on 2007-02-16
Isn't this part of the normal ubutnu update procedure?

If so then this user should already have the latest ALSA drivers.

If not, then how do we go about getting them?

Thanks.

---

### Post by toastedcheese on 2007-02-20
It looks like there are instructions for an Alsa driver update [here]("http://ubuntuforums.org/showthread.php?t=258878&page=2") if you scroll down.

I will try it as soon as I have some free time and don't mind temporarily jeopardizing my audio. :)

---

