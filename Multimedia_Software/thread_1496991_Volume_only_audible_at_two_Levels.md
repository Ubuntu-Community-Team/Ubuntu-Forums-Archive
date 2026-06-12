---
title: "Volume only audible at two Levels"
date: 2010-05-30
forum: Multimedia Software
---

### Post by Zylstra555 on 2010-05-30
Hello, 

My volume does not actually unmute until the volume slider has been moved two levels (or if I press the volume adjuster on my laptop up twice). 
I can not play things very quiet, it all starts at a medium-low volume level. 
How can I regain the initial levels? 

Levels: See the attachment for a better explanation. The level shown at the attachment has NO audio, if I move it up one more, it does.

---

### Post by Zylstra555 on 2010-06-17
Bumpity bump bump bump

---

### Post by lidex on 2010-06-19
> There are a few variables which control how PulseAudio controls the volume. You can either edit /etc/pulse/default.pa (you'll have to be root to do that) to change the behavior for all users, or copy that file to ~/.pulse/default.pa and then edit that file, to change behavior for the current user only.

Open the file mentioned above. Find the row saying "load-module module-udev-detect" and change it to:

load-module module-udev-detect ignore_dB=1

To try your changes, restart PulseAudio with the following command:

killall pulseaudio

PulseAudio will then autospawn (restart itself).

You may find that the above workaround is insufficient, in which case you may configure PulseAudio to control only one mixer control, e.g., PCM (cf. alsamixer). Find the row saying "#load-module module-alsa-sink" and change it to:

load-module module-alsa-sink control=PCM

(remember to remove the # in the beginning of the row!) Optionally replace PCM with the mixer control you want PulseAudio to control.

You will then need to killall pulseaudio as above and allow the daemon to autospawn. 
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by Zylstra555 on 2010-06-20
lidex, 
It worked perfectly. Thank you

---

### Post by lidex on 2010-06-21
Great. Would you mind marking the thread as solved? Click on 'Thread Tools' up top.

---

