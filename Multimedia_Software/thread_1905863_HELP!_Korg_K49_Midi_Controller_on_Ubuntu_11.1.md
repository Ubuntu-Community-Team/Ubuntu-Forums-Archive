---
title: "HELP! Korg K49 Midi Controller on Ubuntu 11.1"
date: 2012-01-07
forum: Multimedia Software
---

### Post by SpiritBear on 2012-01-07
Hello,
I just got a Korg K49 MIDI controller and I'm trying to get it working in Ubuntu 11.1.  I've watched a few videos on YouTube about using MIDI controllers in Ubuntu (there's none for my specific make/model), and they all seem to be using Jack. So I tried Jack, but I'm not sure if I'm doing it correctly, so I'm wondering if anyone could help me. What I've tried:

First I started Jack then went to Connect and then the ALSA tab.
There is a device called Midi-Through Port 0, but nothing showing the name of my controller, so I tried with that. I am trying to use just a basic program for now so I am using AmSynth.  So I connect Midi-Through Port 0 output to AmSynth input.  Then I went to the Audio tab and connected AmSynth to the audio playback.

Then I switch over to AmSynth and mash on my keyboard... nothing.
I press the "Audition" button and it makes a noise, so I know AmSynth is working as far as audio playback.

Soooooo, the fact that Jack says "Midi-Through Port 0" instead of something like "Korg K49" leads me to believe that it's a driver issue.  Am I missing something in the Jack setup?  Do I need to download the Windows drivers from the Korg site and use those somehow?  Any pointers in the right direction would be greatly appreciated. Thanks! :D

---

### Post by llelectronics on 2012-01-08
First of all are you using a usb midi device ? 

If QJackCtl isn't showing your particullary midi device in either Jack-Midi or Alsa-Midi I think you have a problem. Because that normally means there is no driver available for your device.

---

### Post by SpiritBear on 2012-01-08
Yes, the Korg K49 is a usb midi device.

It's showing "Midi Through Port 0" in ALSA, but not the device name like I said, and yes I think it's a driver issue too.  How should I proceed?

---

### Post by SpiritBear on 2012-01-16
anyone?

---

### Post by djembeing on 2012-02-02
Having a similar problem. Any ideas?

---

### Post by Yvanne on 2012-02-24
A new MIDI controller system, the Pulse Surface Controller, allows that air-drummer you know to produce real music by tapping on a table. The newly introduced system, put together by a musician, allows drummers to interface with a computer in a much more organic fashion than ever before. The system turns any surface into a drum head. And the recorded taps may also be changed to emulate any instrument with the correct software. You may read further: [http://www.appisaurus.com/3073-pulse-surface-controller/](http://www.appisaurus.com/3073-pulse-surface-controller/)

---

### Post by fluloulpich on 2012-04-01
Father A Medicine , [http://www.cheaplunestapills.com/](http://www.cheaplunestapills.com/) - lunesta online pharmacy  It has been shown, through studies, to be safe and effective in the short term treatment of insomnia. [generic lunesta](http://www.cheaplunestapills.com/)

---

