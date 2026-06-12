---
title: "Sound and Video not working on my laptop."
date: 2009-01-12
forum: Multimedia Software
---

### Post by samaybhavsar on 2009-01-12
Hi,

I updated my version of Ubuntu from 8.04 to 8.10 but the sound stopped working and the video is also not working.

When I start playing an audio file is asks me to download extra plugins.

GStreamer Extra Plugins
GStreamer ffmpeg video plugin

And then I start installing them it gives me the following error.

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Please help.

---

### Post by sam1948 on 2009-01-12
the "unable to lock" means you are trying to run two installation 
or installation an update at the same time
any way try to look at the system==>administration ==>sound
or some thing like that and other sound device and test it 
(the output devises)

---

### Post by samaybhavsar on 2009-01-14
finally i installed the codecs but still not able to play music files... when i try to test it gets hanged.. even the mp3 player gets hang... but i can hear the start up sound. please help..

---

### Post by samaybhavsar on 2009-01-14
I am getting the following error. What does it mean ??

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

---

### Post by markbuntu on 2009-01-14
You need to change the System/Preferences/Sound to Alsa or pulseaudio. For more about getting your sound working properly go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by samaybhavsar on 2009-01-15
I tried.. it gives a similar error

for ALSA

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resources

for PulseAudio

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

for

---

### Post by samaybhavsar on 2009-01-16
Can anybody help ??

---

