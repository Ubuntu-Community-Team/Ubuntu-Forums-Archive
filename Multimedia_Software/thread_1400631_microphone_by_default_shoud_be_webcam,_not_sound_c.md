---
title: "microphone by default shoud be webcam, not sound card"
date: 2010-02-07
forum: Multimedia Software
---

### Post by cdubet on 2010-02-07
Hello,

After 2 days of struggling, I cannot set the default input as my webcam microphone.
I still have as input my sound card (where no mic is plugged !)

With
```
pulseaudio & pavucontrol
```

I can select the default microphone and set it to the web cam one
But pavumeter continues to use as input the micro alsa pcm on front:0 (ES1371 ...) via DMA (ie the sound card one)

For an unknown reason, pulseaudio applet shows me as default input the web cam micro...

If I type
```
 cat .pulse/default-source
```

I get
alsa_input.usb_device_46d_9a4_1BA5D912_if2_sound_card_0_alsa_capture_0
Which seems to show that the mic should be the web cam one

I tried to set the default mic in .asoundrc but it has done no change

Changes done in Ubuntu menu
**System/preference/sound/sound capture **
did not help :-(


I am wondering if it is not because my version of pulseaudio

pulseaudio volume meter run from the command line (pavumeter) takes the sound card as input but the "pulseaudio volume meter" lauched from pulseaudio applet takes the web cam ... which may shows that there are not using the same code 

version ubuntu 8.04 (hardy)
[I]pavumeter 0.9.3
pulseaudio 0.9.10[/I]

Questions:
**Has somebody an idea to set the web cam microphone as input far ALL applications**
Is it something related to my pulseaudio version ?

Thanks for your help

---

### Post by cwraig on 2010-09-18
I also have this problem, did anyone find a solution?

---

### Post by techclown on 2010-09-18
go to system>prefences>sounds....

choose the input TAB
and choose USB2.0_camera (in my case) your webcam/mic should be listed.

i had same problem this sloved it

---

### Post by SeijiSensei on 2010-09-18
[s]I "solved" it by removing PulseAudio and reverting to plain old ALSA[/s].

Update:  Running Kubuntu 10.10 daily build 9/28

This is probably only relevant for KDE users like me.

In System Settings, choose Multimedia, then Phonon.

Under Audio Capture, select the webcam microphone and pick Prefer, then Apply.  I did this for all three audio items just to be on the safe side.

I found this control panel very confusing because I thought I was supposed to select the device I wanted, not promote or demote it in the list.  I'd select the device, but the Apply button wouldn't light up.  Using Prefer, then Apply made it work.

The camera microphone now works with Pulse.

---

