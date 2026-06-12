---
title: "Mythtv (Mythbuntu) and bluetooth"
date: 2010-09-01
forum: Mythbuntu
---

### Post by davidstoll on 2010-09-01
I'm trying to connect my bluetooth headphones to my myth box, but am not having luck.

The bluetooth applet is running (the little icon).  I can scan for and connect to several different bluetooth devices (headphones, headset with mic, cell phone) but I just don't get audio.

I've tried to follow different threads in this (and other) forums, but have not had any luck.  Can someone help walk me through getting this working...I'm sure you'll need more info.

Obviously, I do want it to work with Mythtv, but I can't even get audio players (VLC) to send audio through bluetooth.

Thanks!

---

### Post by LowSky on 2010-09-01
I found installing an applicaiton called blueman works much better
```
sudo apt-get install blueman
```

---

### Post by davidstoll on 2010-09-01
> **LowSky said:**
> I found installing an applicaiton called blueman works much better
```
sudo apt-get install blueman
```

Thanks, actually, I did try that.  Not to say I did everything correctly, but blueman has been apt-get'ed.  ;)

---

### Post by davidstoll on 2010-09-02
To clarify, I still can't get it to work.

---

### Post by davidstoll on 2010-09-07
It connects but I don't get any sound.

---

### Post by achase79 on 2010-09-12
Have you made sure to set your audio output to the bluetooth instead of the audio card?  I know mythtv has very rigid audio preferences (took me a while to figure out how to send audio via hdmi).

---

### Post by davidstoll on 2010-09-13
> **achase79 said:**
> Have you made sure to set your audio output to the bluetooth instead of the audio card?  I know mythtv has very rigid audio preferences (took me a while to figure out how to send audio via hdmi).

Yes, I set the device to: ALSA:bluetooth and it doesn't particularly like it.  When I try to start a video in Mythtv, it sort of sits there "please wait..." and when the video finally loads (about 1 minute or so), there is no audio.

I would still like to know how to get it to work, but I'm thinking that switching it back and forth every time I want to use the normal speakers or bluetooth...it's kind of a pain and seems to be totally non-automatic or non-simultaneous.

Maybe a separate wireless (non bluetooth) headset is the way to go.  Just split the audio out and turn down the speakers when I want to use the headset.  Unfortunately, pretty much all wireless headsets are giant monstrosities and aren't like the earbud type that would be most comfortable while laying down.

:(

---

### Post by achase79 on 2010-11-16
I found this [website]("http://it.toolbox.com/blogs/locutus/mission-impossible-connect-bluetooth-headset-to-linux-35365").  Maybe this will help you.

---

### Post by Dan_R on 2010-11-17
I see this thread was bumped and dated, but there isn't much info on this subject so I will put this out there.

I recently setup a bluetooth headset (Samsung SBH600) to do basically what you want, but I was unable to get it working with ALSAs basics, so I tried PulseAudio. With Pulse you can make it output to both a regular line out on the machine, and a bluetooth headset simultaneously. All you would have to do using this method is when you want to use bluetooth, just turn on the headset and hit the pairing button on it and within 5 seconds will output sound.

From what I remember through Synaptic I had to install the pulseaudio and pulseaudio-module-bluetooth packages. Once installed go into the Pulse Audio Preferences and choose Simultaneous Output and check the box for Add virtual device.

Ensure your device is paired, and go into the PulseAudio Volume Control and go into the Config tab. Hopefully you should see your bluetooth headset, if its going to be used just for listening, change the profile to A2DP for best audio. Change your normal audio hardware profiles to what you would like. 

If you go to the Output Devices tab you should see your hardware setup and the simultaneous output should be there. If you go to the Playback tab and choose an app to play music, it should show up there and you can choose what profile to use for specific ones.

I don't know if there's anything else, unless you need to go into the regular Sound preferences and change the Output to Simultaneous, although I think the different GUIs link together.

Don't forget to change the profile in MythTV to Pulse:default, I think, depending on your Myth release.

---

