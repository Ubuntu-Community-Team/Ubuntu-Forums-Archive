---
title: "Can record Skype caller OR myself, not both with QjackCtl Audacity"
date: 2013-05-05
forum: Multimedia Software
---

### Post by elaterite on 2013-05-05
Hi!

Problem: 
Using QjackCtl, Audacity, and Skype, I can record the caller OR myself, but not both. (And I apologize for cross postings, but I've been trying to solve this for over a month and am getting desperate.)

Options:
No, I do not want to use a third party specific Skype call recorder.

Equipment / Hardware / Software:
Dynamic microphone
Firewire mixer
ASUS P5QC motherboard with onboard Realtek ALC 1200, 8-Channel High-Def Audio 
Ubuntu Studio 13.04
Skype 4.1
Audacity 2.0.3 (repository)
QjackCtl 0.3.9
PulseAudio Volume Control

Please see the PDF (if not posted below) at this link:
[ http://electricnevada.org/pics/record.pdf]("http://electricnevada.org/pics/record.pdf")

Referring to the photos on the PDF, from l-r, top to bottom:
Each photo shows Audacity, PulseAudio Volume Control (each tab, indicated by the small red circle: Playback, Recording, Output Devices, and Input Devices), and QjackCtl "Connections" during an active Skype test call when the women is speaking.

The first four photos are the default open for all of the software and I can immediately record the Skype side of the call with Audacity.

The fifth photo, at the bottom of the PDF, shows the only change I need to make to record myself--but then I loose the ability to record the Skype side of the call. 

As you can see it is solely dependent on the "Recording" tab option of "Monitor of Built-in Audio Analog Stereo" (large red circle) where I can record the caller (as in photo #2), or, as in the fifth photo at the bottom of the page, "Jack Source (PulseAudio JACK Source)" option where I can record myself but not the caller.

Question:
How do I get “ALSA plug-in [audacity]: ALSA Capture from” to capture from both "Monitor of Built-in Audio Analog Stereo" AND "Jack Source (PulseAudio JACK Source)"? It seems I need to added these devices to the QjackCtl "Connections" panel so I can connect them together, yes/no? If so, I've not a clue how to do that.

The command line doesn't scare me, but I'm only a cookbook recipe follower, so I need precise instructions.

Also, I'd like to know how to identify, at the command line, the various output streams from my onboard sound card.

Any help would be greatly appreciated—thanks!

---

