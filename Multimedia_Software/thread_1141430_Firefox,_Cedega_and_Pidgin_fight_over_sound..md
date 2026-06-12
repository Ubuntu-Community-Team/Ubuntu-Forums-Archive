---
title: "Firefox, Cedega and Pidgin fight over sound."
date: 2009-04-28
forum: Multimedia Software
---

### Post by Winterhart on 2009-04-28
In an effort to get properly multi-application sound, I followed the pulseaudio howto [http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578") here.  Individual applications, tested independently, have correct sound.  It's when running more than one app at once that things start to get hairy.

If I play something with sound in Firefox (youtube, an unfortunate flash ad, mlb.com, &c.) then when I start up a game in Cedega, I have no sound at all.  I have to close Firefox before I can have sound in my game.  Same goes for the other way 'round - if I actually want to watch a video, I have to close Cedega.

Pidgin has some of the same problems: if I have a game running, I have no sound when sending & receiving IMs.

Does anyone know how to make this system have multi-application sound that ACTUALLY works? :(

---

### Post by lovinglinux on 2009-04-28
Set all your audio settings to ALSA instead of pulseaudio. This should solve the problem. Pulseaudio is problematic.

---

### Post by Winterhart on 2009-04-29
They don't have pulseaudio settings.  I can't see where Firefox has any way to specify a sound application at all, Pidgin certainly doesn't, and Cedega lets you choose only between alsa and oss.

---

### Post by lovinglinux on 2009-04-29
> **Winterhart said:**
> They don't have pulseaudio settings.  I can't see where Firefox has any way to specify a sound application at all, Pidgin certainly doesn't, and Cedega lets you choose only between alsa and oss.

Set in the system sound settings - "System >> Preferences >> Sound"

---

### Post by Winterhart on 2009-04-29
The HowTo specifically said not to do that :(

[I]
4. Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
Note: Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/I]

---

### Post by lovinglinux on 2009-04-29
> **Winterhart said:**
> The HowTo specifically said not to do that :(

[I]
4. Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
Note: Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/I]

Don't worry. Select ALSA and you will be fine. The detection feature sometimes choose pulseaudio automatically. That's why you can't play audio on multiple programs at the same time. I'm running everything with ALSA fo almost a year now, without sound issues.

---

### Post by Winterhart on 2009-04-29
I'm sorry if I'm being dense, but this part just doesn't make sense to me:
[I]
The detection feature sometimes choose pulseaudio automatically. That's why you can't play audio on multiple programs at the same time.[/I]

With ALSA, to my understanding, there is no multi-application audio support.

With PulseAudio, there is [supposed to be].

So why would setting everything back to ALSA help?

---

### Post by lovinglinux on 2009-04-29
> **Winterhart said:**
> I'm sorry if I'm being dense, but this part just doesn't make sense to me:
[I]
The detection feature sometimes choose pulseaudio automatically. That's why you can't play audio on multiple programs at the same time.[/I]

With ALSA, to my understanding, there is no multi-application audio support.

With PulseAudio, there is [supposed to be].

So why would setting everything back to ALSA help?

[http://ubuntuforums.org/showthread.php?t=924590](http://ubuntuforums.org/showthread.php?t=924590)

---

### Post by psyke83 on 2009-04-29
> **lovinglinux said:**
> Don't worry. Select ALSA and you will be fine. The detection feature sometimes choose pulseaudio automatically. That's why you can't play audio on multiple programs at the same time. I'm running everything with ALSA fo almost a year now, without sound issues.

Changing to ALSA output in System -> Preferences -> Sound will not do what you think:

[LIST]
[*]This application only control the settings for GStreamer applications (Totem, Rhythmbox, etc.) - Firefox and many other applications won't be affected. 
[*]The ALSA libraries have been patched, since Intrepid, to transparently map audio to the "pulse" device - this means that if you select ALSA output, PulseAudio will continue to play audio in your GStreamer applications, but they will play through PulseAudio using ALSA "emulation" instead of using the native PulseAudio output.
[/LIST]

Winterheart, I suggest you read my tutorial again, and pay attention to the Appendixes, as they deal precisely with your problem.

---

### Post by lovinglinux on 2009-04-29
> **psyke83 said:**
> Changing to ALSA output in System -> Preferences -> Sound will not do what you think:

[LIST]
[*]This application only control the settings for GStreamer applications (Totem, Rhythmbox, etc.) - Firefox and many other applications won't be affected. 
[*]The ALSA libraries have been patched, since Intrepid, to transparently map audio to the "pulse" device - this means that if you select ALSA output, PulseAudio will continue to play audio in your GStreamer applications, but they will play through PulseAudio using ALSA "emulation" instead of using the native PulseAudio output.
[/LIST]

Winterheart, I suggest you read my tutorial again, and pay attention to the Appendixes, as they deal precisely with your problem.

Sorry for my misconceptions and thanks for explaining it so clearly. I just suggested to change to ALSA, because it worked for me on Hardy and Jaunty. Anyways, I will redirect future posts about this to your tutorial and will read it later. Seems to be very instructive.

Thanks again.

---

