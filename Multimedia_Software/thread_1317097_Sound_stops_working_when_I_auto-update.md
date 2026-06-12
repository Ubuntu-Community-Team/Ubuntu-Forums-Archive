---
title: "Sound stops working when I auto-update"
date: 2009-11-06
forum: Multimedia Software
---

### Post by Darkness Falls on 2009-11-06
Hi there everyone!

I'm running Jaunty on my laptop, having recently migrated over to Ubuntu from Windows, and I seem to be having trouble getting the sound to stay working. I had trouble with it initially, but just about managed it; then Update Manager recommended I download some files, and in doing so, I somehow lost all sound again.

I fixed that by updating the ALSA drivers to the latest version I could find mention of (1.0.21), and that worked perfectly - it even recognised the headphones, which it hadn't been doing previously. Then, a few days ago, I made another download following Update Manager's recommendation, and it forgot how to turn off the sound coming through the speakers when I was using headphones. Then, yesterday, Update Manager said there were yet more files I should download, which I did; today, I have no sound at all.

Please note, this isn't a matter of upgrading to Karmic Koala and having teething trouble; these are simply the files that Update Manager thinks I should have, presumably as part of an automated process. The problem is, I don't know enough about Ubuntu (or Linux in general) to know where to go from here. From reading around a little, I gather there are conflicts sometimes between Pulseaudio and ALSA; could the updates be changing Pulseaudio so it no longer works nicely with ALSA? If so, is there a way to roll back the updates, or otherwise find a work-around?

Thanks in advance!

D.F.

---

### Post by Darkness Falls on 2009-11-07
Okay, following the above, I've uninstalled Pulseaudio and installed esound instead, rebooted and set everything in System>Preferences>Sound to ALSA; unfortunately, the Test function returns the following:

```
audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback.
```

I then tried running alsamixer from the Terminal, only to get this:

```
cannot open mixer: No such file or directory
```

Alsaconf seems to work fine, it finds my sound cards perfectly and says that it's configured okay; but then I run *aplay -l* and get:

```
aplay: device_list:223: no soundcards found...
```

...and now I'm confused. How can it say the sound card is perfectly configured when it apparently can't find it? Any thoughts?

D.F.

---

### Post by ken78724 on 2009-11-07
Darkness
have you reviewed Markbuntu's sticky or almost sticky on sound. His overview covers most all ?s on a step by step basis. My compliments on clear enunciation of where you are; can not help you as I just installed Ubuntu Studio 9.10 Karmic & did not have sound before and may not have it now either.

---

### Post by Darkness Falls on 2009-11-08
Solved! I ended up setting System>Preferences>Sound to Autodetect and following the solution at the bottom of the first page of this thread here:

[http://ubuntuforums.org/showthread.php?t=1236208](http://ubuntuforums.org/showthread.php?t=1236208)

...and sound now works again, headphones included! The only thing now is wondering if it'll be safe to use Update Manager again now that Pulseaudio is gone, or whether it'll try and mess up ALSA again, but we'll cross that bridge when we come to it. In the meantime, I don't suppose anyone knows of a way to undo the changes made by Update Manager, in case this happens again?

Thanks for the pointer, though, Ken; Markbuntu's guide was actually the one I used when I got the sound working the first time, a few months ago!

D.F.

---

### Post by Darkness Falls on 2009-11-17
Agh, I held off from auto-updating for a week because I was afraid that something like this would happen. When I eventually relented, I made sure to remove all the ticks from the pulseaudio-related options, in case it tried to reinstall pulseaudio again and undid all my work with ALSA and ESD. The only things I updated were the kernel and qt4, and the packages associated with them.

Problem is, of course, now the sound's stopped working again. The best I can guess is that something in the kernel update has overridden the previous settings. Does anyone know where to look to change the settings back? I don't think there are any newer versions of the ALSA drivers out, although if someone could confirm that would be helpful (I'm currently running 1.0.21). Does anyone have any suggestions as to why this keeps happening?

Also, if this is likely to keep happening, is there a way to turn off auto-update? Because this is really starting to annoy me now.

Thanks for any input you can give.

D.F.

---

