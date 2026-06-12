---
title: "Bluetooth headset and skype"
date: 2008-09-29
forum: Multimedia Software
---

### Post by gloomygod on 2008-09-29
Hi there,

I have installed Ubuntu 8.04 in my Medion Akoya laptop (MSI wind clone).

I've tried to configure a bluetooth headset, following  almost every guide out there.

The guide with best results has been this one:

[http://ubuntuforums.org/showthread.php?t=786640](http://ubuntuforums.org/showthread.php?t=786640)

There are in this forums another guide, that pushes it a little further, and uses PulseAudio,, but it does not work for me (Pulseaudio itself, does not work very fine for me. It does not want to route audio through my headset).

So, I'm stucked at this point:

-My BT dongles works fine.
-The headset is paired.
-I have another alsa soundcard.
-I can record and play audio without problem though my headset using aplay or arecord from console.

But the problem comes when I try to use the BT device with skype: It starts sounding, and gets disconnected after a fey seconds (like 5-10). I can't even record the message on the test call.

So, do you think this could be a problem of my headset?. It works fine in windows though.

Could it be a problem of skype?

Thx a lot.

---

### Post by TremerePuck on 2008-10-04
Same problem here. My Skype starts calling and gets stuck ringing non-stop and freezes.

Do other programs like Amarok, mplayer, or kaffeine work for you? They play sound briefly then freeze on me like skype.

---

### Post by markbuntu on 2008-10-04
I have just recently added a special SKYPE with PulseAudio section to my general sound troubleshooting guide here, there is also a section about USB Headsets etc that may help with your bluetooth problem:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Other parts of my guide may give you information about how pulseaudio and alsa work to help you diagnose your problem better.

---

### Post by TremerePuck on 2008-10-05
I've had no luck getting PulseAudio to work. I keep getting that it can't connect to the PulseAudio server.

Without PulseAudio, using only ALSA, I can get the headset to work with aplay and arecord, but nothing else.

So I don't think your troubleshooting guide will help me. But thanks. =o)

---

### Post by minky311 on 2008-10-06
When you open a terminal by going to Applications->Accessories->Terminal and typing in alsamixer is there an error?
Make sure you are using pulseaudio when you try this.
Post the error here if there is one.

---

### Post by TremerePuck on 2008-10-23
I don't really need pulseaudio though. Just going to use it for Skype.

---

