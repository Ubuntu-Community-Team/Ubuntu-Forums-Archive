---
title: "Mic troubles"
date: 2008-10-14
forum: Multimedia Software
---

### Post by Yokaze on 2008-10-14
Ok I've up and down this forum and numerous other places looking for a solution and nothing has working. I'm using an AC'97 Audio Controller, with a normal desktop microphone on hardy. I have pulseaudio installed and I can hear sounds from every application I just can't put any audio in. I've tested it with both skype and sound recorder to no avail. I've checked and rechecked all of the volume settings and they are max where need be. Does anyone have any idea what I'm doing wrong? Thanks

---

### Post by theirishfozz on 2008-10-14
I use oss and had some trouble getting sound working. All I can suggest is fiddling with the settings in your mixer. I had to mute a lot of stuff before mic would work and set my pink-in as an input. Try looping your mic through to your speakers with a shell app. I dont have any pulse experience so I cant help with that.

Alternatively if mic is necessary you could try switching to OSS or ALSA.

---

### Post by markbuntu on 2008-10-14
I was about to add this to my 10,000 page guide to sound but you get to try it first:

To control your input for recording you can set your System/Preferences/Sound/Audio Conferencing/Sound capture to PulseAudio Sound Server and use PulseAudio Volume Control/Input Devices to choose which device to record from. This is very handy as you can quickly switch between  your sound card pcm stream or microphone to your webcam mic or usb headset. All you need to do is open the PulseAudio Volume Control/Input Devices and right click on any available device to make it the default then open the application. Just make sure that "capture" is enabled and turned up in the panel volume control or your alsa based mixer

You should also now have a PulseAudio Volume Meter (capture) you can use to test your microphone or other capture inputs available in your sound mixer or volume control.  Once you have chosen your default device, you can open sound recorder and record it. If you choose a monitor device, you can record whatever is going through the comparable Output Device. 

If you are using a microphone for recording and wish to not hear the microphone input to prevent feedback, you can just mute the microphone playback in the panel volume control or ALSA sound mixer. It is the Capture settings that are the only important ones for recording.

---

