---
title: "Can't turn volume down below 24% in ubuntu 10.10"
date: 2011-04-16
forum: Multimedia Software
---

### Post by twtgd09 on 2011-04-16
Hey, ever since installing ubuntu maverick meerkat, ive  been having an issue with the sound control, whenever i turn the sound down below 24%, it cuts out completely, and it goes from relatively loud, to silent. Has anyone else had this problem? where should i start troubleshooting?

---

### Post by twtgd09 on 2011-05-06
Bump

---

### Post by lidex on 2011-05-06
From the ubuntu wiki:
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

