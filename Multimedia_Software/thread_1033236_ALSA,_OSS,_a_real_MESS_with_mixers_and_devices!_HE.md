---
title: "ALSA, OSS, a real *MESS* with mixers and devices! HELP!"
date: 2009-01-07
forum: Multimedia Software
---

### Post by asbesto on 2009-01-07
Hi, 

I have a normal PC, with a normal audio board; I connect a microphone, a line in, and an audio output.

So I expect to have controls for volume, line in, mic, capture, pcm out, and FEW ELSE THINGS like cd and so on...

And here come the problems:

1) Opening my Gnome mixer, I have TONS of controls! Line, Front Line, Mic, Front Mic, also I have 3 Capture sources, a pair of weird IEC598 controls, Aux, and other stuff!

2) Also, in gnome mixer, I have to check between many devices. In this computer, I have "HDA Nvidia (Alsa mixer)" and "Analog Devices AD1988 (OSS)".  

But I remember using of OSS was discouraged as obsolete years ago! Why is already there?



The real mess is that I put a LINE IN cable on to record something, and

1) moving any LINE IN slide or switch doesn't change anything on my audio capture program (e.g. Audacity)

2) I can LISTEN to the LINE IN thru the earphones connected to the soundcard output, so I think the line in is correctly connected!!! but NO CAPTURE at all.

3) Moving CAPTURE slides will vary the sound volume output, but no capture at all

4) Moving other slides (e.g. IEC598, DIGITAL ?!?) will OPEN the capture, but I really don't know how they act

5) Using the MIC IN is a real problem, because all this is different!!!



I wonder WHY a single soundcard with a FEW input is so complicated to use.

Also, there is difference between, for example, Gnome Mixer and alsamixer under console. 



Is there any way to put all this more simple? for example, removing the old OSS support ? or something else?

please someone help, as I'm becoming really MAD on this (my IBM T40 Laptop show me FIFE (!) sound cards!!!!!!!

i'm DESPERATE

:(

---

### Post by markbuntu on 2009-01-07
Well, for one thing your sound card is not so simple as you suppose. There are lots of connectors for you to plug things in to, some are on the front and some are on the back and there are little switches in some of those connectors that say when something is plugged in to it. Plus you have digital which is the IEC958. And this is all different for every different machine so it tends to get complicated.

Put simply, the gnome-alsamixer puts every control on one page while the sound mixer in your panel breaks it up into sections for playback recording switches and options. You can choose what is displayed in the panel mixer in Edit/preferences and in the gnome-alsamixer in Edit/Sound Card Properties. For now you should just go to those menus and select everything so you can see it all.

In the panel volume control the Playback section is for what goes to your speakers and/or headphones. The recording section is for recording. In the switches section you will see switches for things like PCM Capture, Line-in capture, Mic boost, Mic Boost capture, Mic Capture, etc. These capture switches must be on if you are going to record from the input. You may also have an Options section. Many sound cards also use the mic and line in jacks for surround sound output and that can be selected here.

In the gnome-alsamixer the capture switches are the rec switches below the sliders. These are the sliders you need to use for that particular device when recording with the rec switch on. If you open both the mixers you will see the other one change when you change something so really they are both doing the same thing.

With some sound cards if you enable the IEC958/SPDIF digital, whatever you are recording is shunted to the digital output and made unavailable to your recording application. Some sound cards shunt all sound to the digital output when it is selected. With some sound cards, the switches are backwards from what you would expect. 

Manufacturers are very lazy about publishing how they have programmed their sound chips so the driver writers are pretty much reduced to guessing how they did it and reduced to waiting for users to tell them what is going on so they can fix it.

The OSS device is necessary as there are still applications that look for OSS but really there is only one you need to concern yourself with and that is the actual hardware device. The rest are virtual devices created so applications can find them.

Don't feel so bad, I have 23 devices in my list.

If you want some help for setting up your sound, go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

