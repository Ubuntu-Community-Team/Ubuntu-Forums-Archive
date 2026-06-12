---
title: "Bluetooth headset records but won't play back"
date: 2009-12-05
forum: Multimedia Software
---

### Post by curlybap on 2009-12-05
Hi,

My cheap, store-brand Bluetooth headset won't play back from Ubuntu 9.10 Karmic.  It works fine with a Bluetooth phone.

It works fine for recording but when you try to play a sound from any program the program hangs or refuses to play.

Pulseaudio detects the headset and it is shown as an input and output device in Volume Control.

Any suggestions to fix this one?

---

### Post by grimhen on 2009-12-13
I have the same problem as you. I have not idea what is wrong. I test this on Skype and mic works very well over bluetooth but i hear no sound in my headset. Something freeze sending sound.

My headset is Logitech Mobile Traveller and maybe its a device problem (protocol ?) nor pulseaudio ? I want to check this tomorrow with different device.

One more thing with this, i check the stats from Blueman and i have down speed over 16 KB/s and upload speed is only 16 B/s so i think that my PC doesnt send any of data to headset.

---

### Post by curlybap on 2009-12-13
A few days ago I found this bug on launchpad - [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/444017]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/444017").  No help though.

---

### Post by grimhen on 2009-12-15
I've tested this with different headset (Plantronics M2500) and nothing was changed. Microphone working but playback wasn't :(

---

### Post by grimhen on 2009-12-15
So ... its working!

I actually testing this with three different bluetooth adapter. And i have only one conclusion. The problem is in Pulseaudio or bluetooth kernel driver because they don't support these devices correctly.

All of these adapters runs "out-of-box" in Linux based OS when you want to use them to transfer data from PC to cellular phone and vice versa.

First I tested D-Link System DBT-122 Bluetooth. As i wrote before its only work in one-way communication. Microphone works, playback not. So i have exactly the same experience as you.

Next I used Gembird adapter detected by the system as Integrated System Solution Corp. KY-BT100 Bluetooth Adapter. Few years ago I tested this with BTSCO module and its partially works (microphone don't record). With pulseaudio and blueman it has a problem with headset service. Its connect fine but it doesn't show in PulseAudio Volume Control.

Finally I used very cheap (it cost something about 2$) bluetooth dongle. It's detected by system as Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode). In spite of very low link quality on this dongle(blueman shows only 10% link quality vs 100% link quality with D-Link adapter) it ... WORKS! :D

I testing Skype right now and I have no problem with connection. Playback and microphone working together, sound quality is good (maybe it will be better if link quality will be better too). After few years of playing around with BTSCO module, .asoundrc, alsa and Skype it starts working as I expected.

Curlybap i think you must change your bluetooth adapter because your dongle is not supported correctly at this moment.

---

### Post by curlybap on 2009-12-16
That's interesting - my dongle is also a D-Link DBT-122.

Glad to hear you got it working; might see if I can grab another dongle in the January sales! :)

---

