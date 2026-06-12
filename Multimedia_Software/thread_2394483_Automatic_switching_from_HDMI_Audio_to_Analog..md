---
title: "Automatic switching from HDMI Audio to Analog."
date: 2018-06-17
forum: Multimedia Software
---

### Post by blacksmithkazuma on 2018-06-17
I have been looking for days to see if I can find a fix. I am running 18.04 and when I plug my hdmi cable in to watch a movie or whave have you I have to go into pulse audio and manually switch the audio output. Is there another why besides that and the thousands of scripts that are all over the net. Any help would be great. thanks.

---

### Post by nik.charles on 2018-06-22
I do not have hdmi to check how well this would work, but should work similar to usb removable devices

With hdmi plugged in, get the name used for Pulseaudio
```

pactl list cards | grep Name
```
Set Pulseaudio default audio device to hdmi
```
pacmd set-default-sink <name>
```
to check default is set correctly
```
cat /config/pulse/*sink
```

If hdmi is connected and active, any playback started should default to hdmi
but anything playing on another audio device would not switch to hdmi

There is a Pulseaudio module switch-on-connect
[https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#index65h3](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#index65h3)

suggest if want to make changes to Pulseaudio modules to copy system file to home folder and leave original default alone
```
cp /etc/pulse/default.pa ~/.config/pulse/default.pa
```
Open new file in text editor of choice and add this line at end:
```
load-module module-switch-on-connect
```
save and restart Pulseaudio
check if it is loaded with
```
pactl list short modules
```

---

