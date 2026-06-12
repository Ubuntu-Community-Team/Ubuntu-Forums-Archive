---
title: "Sound not playing and ouput devices dot not detect inbuilt-audio"
date: 2018-10-16
forum: Multimedia Software
---

### Post by gypsycosmonaut on 2018-10-16
Audio was working perfectly fine yesterday, but I was tinkering around with it and installed audacity and pavucontrol. I wanted to record the streaming output sound playback. I selected something in recording section in pavucontrol and recoded the audio, worked fine. 

But next I know, I rebooted my machine and sound is not working. I tried recording streaming audio of ouput device in audacity, and it is working, the audio is being recorded in audacity but I am not able to hear any audio in my earphones. 

PS: my earphones are working fine. Checked.

Here is the information of my alsa

[http://www.alsa-project.org/db/?f=421835cac6e35636529a2c938cc6f89aeb41cbf8](http://www.alsa-project.org/db/?f=421835cac6e35636529a2c938cc6f89aeb41cbf8)

---

### Post by Autodave on 2018-10-18
After you recorded something, did you try playing it back with Audacity?  Do the VU meters show that there is something playing?  If so, then look in Audacity: Edit -> Preferences -> Devices -> Playback Device and see what is chosen there. Normally, *default* is what you need unless you have this through HDMI or something else.

---

### Post by nik.charles on 2018-12-20
your alsa-info looks mostly ok 

but it is showing another sound server (RoarAudio) installed and running
according to website, latest version of this is: v1.0beta12 Prerelease: Thu Nov 06 2014 12:09
beta software and no updates for 4 years is not good sign
Pulseaudio has had many updates and changes since v5 in 2014 to current v12, so no surprise RoarAudio does not work well with it 

I suspect that this is hijacking audio stream playback from Pulseaudio 
possibly you installed RoarAudio to get audacity recording? (you do not say what recording source audacity is using)
suspect that if you turn off/disable/remove RoarAudio, then Pulseaudio playback will be ok again

Pulseaudio usually has a "Monitor of" any audio playback stream that audacity should be able to record from
The monitors do not always show in "pavucontrol --tab 4" Input Devices
may need to change the drop down menu at bottom of Pulseaudio window ("show:") to stop them being hidden

---

