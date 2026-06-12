---
title: "volume slider not working properly"
date: 2011-05-07
forum: Multimedia Software
---

### Post by wim.glenn on 2011-05-07
hi there, i've just put on a fresh install of natty narwhal, and the volume slider in the top right corner doesn't work.  if i move it all the way left to 0, the sound goes off, but anything non-zero seems to be full volume.  anyone else have this problem?  i searched a bit , tried fiddling around in alsamixer , and gconf-editor -> apps->gnome_settings_daemon->volume_step but couldn't get any useful result.

---

### Post by lidex on 2011-05-11
From ubuntu wiki:
> Volume range anomalies

The latest version of PulseAudio tries to control the volume of the sound card using its mixer controls. Usually this works just fine, but in some cases this does not work properly. (Whether this is PulseAudio's or ALSA's fault is beyond the scope of this wiki page. Some more background information is here.)

Diagnosis

You experience any of the following:

    Jumps in volume, e g if everything below 20% is muted, and 21% is very loud.
    Overdriven (distorted sound) if the volume is set above a certain (low) level
    No volume changes in parts of the range, e g if 20% is just as loud as 70%. 

Fix / Workaround

There are a few variables which control how PulseAudio controls the volume. You can either edit /etc/pulse/default.pa (you'll have to be root to do that) to change the behavior for all users, or copy that file to ~/.pulse/default.pa and then edit that file, to change behavior for the current user only.

Open the file mentioned above. Find the row saying "load-module module-udev-detect" and change it to:

load-module module-udev-detect ignore_dB=1

To try your changes, restart PulseAudio with the following command:

killall pulseaudio

PulseAudio will then autospawn (restart itself).

You may find that the above workaround is insufficient, in which case you may configure PulseAudio to control only one mixer control, e.g., PCM (cf. alsamixer). Find the row saying "#load-module module-alsa-sink" and change it to:

load-module module-alsa-sink control=PCM

(remember to remove the # in the beginning of the row!) Optionally replace PCM with the mixer control you want PulseAudio to control.

You will then need to killall pulseaudio as above and allow the daemon to autospawn. 

---

### Post by wim.glenn on 2011-05-16
thanks , it worked !!

---

### Post by lidex on 2011-05-16
Great. Please mark the thread solved using 'Thread Tools' up top.

---

